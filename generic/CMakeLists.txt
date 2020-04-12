#
#  satnogs-flowgraphs: SatNOGS GNU Radio flowgraphs
#
#  Copyright (C) 2020
#  Libre Space Foundation <http://libre.space>
#
#  This program is free software: you can redistribute it and/or modify
#  it under the terms of the GNU General Public License as published by
#  the Free Software Foundation, either version 3 of the License, or
#  (at your option) any later version.
#
#  This program is distributed in the hope that it will be useful,
#  but WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#  GNU General Public License for more details.
#
#  You should have received a copy of the GNU General Public License
#  along with this program.  If not, see <http://www.gnu.org/licenses/>
#

set(flowgraphs
    afsk1200_ax25.grc
    bpsk.grc
    cw_decoder.grc
    example_flowgraph.grc
    fsk.grc
    iq_receiver.grc
    sstv_pd120_demod.grc
)

foreach(grc_file ${flowgraphs})
    get_filename_component(fname ${grc_file} NAME_WE)
    add_custom_command(OUTPUT "satnogs_${fname}.py"
        COMMAND grcc ${grc_file} -o ${CMAKE_CURRENT_BINARY_DIR}
        WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
        DEPENDS ${grc_file}
    )
    
    add_custom_target(${fname} ALL  DEPENDS "satnogs_${fname}.py")
    list(APPEND generated_flowgraphs 
        "${CMAKE_CURRENT_BINARY_DIR}/satnogs_${fname}.py"
    )
endforeach()
    
install(
    PROGRAMS
    ${generated_flowgraphs}
    DESTINATION bin
)
