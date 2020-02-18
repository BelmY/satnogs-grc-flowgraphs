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
    bpsk_ax25.grc
    cw_decoder.grc
    example_flowgraph.grc
    fsk_ax25.grc
    iq_receiver.grc
    sstv_pd120_demod.grc
)
message("Compiling GRC SatNOGS flowgraphs…")
foreach(grc_file ${flowgraphs})
    message("Compiling " ${grc_file})
    execute_process(COMMAND grcc ${grc_file} -o ${CMAKE_CURRENT_BINARY_DIR}
                    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
                    RESULT_VARIABLE ret
    )

    if(NOT (ret STREQUAL "0") )
        message(FATAL_ERROR "grcc failed to compile ${grc_file}")
    endif()
endforeach()

install(
    PROGRAMS
    ${CMAKE_CURRENT_BINARY_DIR}/satnogs_afsk1200_ax25.py
    ${CMAKE_CURRENT_BINARY_DIR}/satnogs_bpsk_ax25.py
    ${CMAKE_CURRENT_BINARY_DIR}/satnogs_cw_decoder.py
    ${CMAKE_CURRENT_BINARY_DIR}/satnogs_example_flowgraph.py
    ${CMAKE_CURRENT_BINARY_DIR}/satnogs_fsk_ax25.py
    ${CMAKE_CURRENT_BINARY_DIR}/satnogs_iq_receiver.py
    ${CMAKE_CURRENT_BINARY_DIR}/satnogs_sstv_pd120_demod.py
    DESTINATION bin
)
