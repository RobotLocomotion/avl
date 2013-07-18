

# if ifort 
#set(SECOND = second_ifc.f)
# else
set(SECOND second_g77.f)
# endif

add_executable(avl 
		   avl.f aoper.f amode.f amass.f asetup.f 
		   amake.f ainput.f aoutput.f aero.f atrim.f atpforc.f 
		   aic.f cdcl.f airutil.f autil.f 
		   aplotvl.f aplottp.f aplotmd.f limits.f 
		   pltops.f hidden.f 
		   plsubs.f 
		   userio.f plutil.f arrow3d.f getvm.f 
		   matrix.f spline.f sgutil.f 
		   ${SECOND} )
target_link_libraries(avl plotlib eispack)

pods_install_executables(avl)
