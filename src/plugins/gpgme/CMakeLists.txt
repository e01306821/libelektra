include (LibAddPlugin)

if (DEPENDENCY_PHASE)

	find_package (LibGpgme QUIET)
	if (NOT LIBGPGME_FOUND)
		remove_plugin ("gpgme" "GPGME development files not found")
	endif ()

endif ()

set (GPGME_SOURCE_FILES keylist.h keylist.c gpgme.h gpgme.c)

add_plugin (gpgme SOURCES ${GPGME_SOURCE_FILES} INCLUDE_DIRECTORIES ${LIBGPGME_INCLUDE_DIRS} LINK_LIBRARIES ${LIBGPGME_LIBRARIES} ADD_TEST)
