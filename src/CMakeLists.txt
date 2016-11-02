#############################################################################
#
#  AVL
#
#  Copyright (C) 2002 Mark Drela, Harold Youngren
#
#  This program is free software; you can redistribute it and/or modify
#  it under the terms of the GNU General Public License as published by
#  the Free Software Foundation; either version 2 of the License, or
#  (at your option) any later version.
#
#  This program is distributed in the hope that it will be useful,
#  but WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#  GNU General Public License for more details.
#
#  You should have received a copy of the GNU General Public License
#  along with this program; if not, write to the Free Software
#  Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.
#
#############################################################################

set(AVL_SRCS avl.f aoper.f amode.f amass.f asetup.f amake.f ainput.f
  aoutput.f aero.f atrim.f atpforc.f aic.f cdcl.f airutil.f autil.f aplotvl.f
  aplottp.f aplotmd.f limits.f pltops.f AVLPLT.INC hidden.f plsubs.f
  AINDEX.INC userio.f plutil.f arrow3d.f MASKS.INC getvm.f AVL.INC matrix.f
  spline.f sgutil.f second_g77.f $<TARGET_OBJECTS:eispack>)
add_executable(avl ${AVL_SRCS})
set_target_properties(avl PROPERTIES VERSION ${PROJECT_VERSION})
target_link_libraries(avl plt)

export(TARGETS avl FILE "${CMAKE_BINARY_DIR}/avl-targets.cmake")

install(TARGETS avl EXPORT avl-targets DESTINATION ${CMAKE_INSTALL_BINDIR})
install(EXPORT avl-targets DESTINATION ${CMAKE_INSTALL_DATADIR}/${PROJECT_NAME})

set(AVL_COPYING gpl.txt)
install(FILES ${AVL_COPYING} DESTINATION ${CMAKE_INSTALL_DOCDIR}
  RENAME COPYING)

# Disabled due to build errors.
# set(DTEST_SRCS dtest.f)
# add_executable(dtest ${DTEST_SRCS})
