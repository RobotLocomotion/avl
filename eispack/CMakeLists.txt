#############################################################################
#
#  EISPACK
#
#  Copyright (C) 1983 Burton S. Garbow
#
#############################################################################

set(EISPACK_SRCS eispack.f)
add_library(eispack OBJECT ${EISPACK_SRCS})
