# Copyright (c) Martin Schweiger
# Licensed under the MIT License

add_library(LuaConsole SHARED
	LuaConsole.cpp
	LuaConsole.rc
	ConsoleInterpreter.cpp
	ConsoleCfg.cpp
)

target_include_directories(LuaConsole
	PUBLIC ${ORBITER_SOURCE_SDK_INCLUDE_DIR}
	PUBLIC ${MODULE_COMMON_DIR}
	PUBLIC ${ORBITER_SOURCE_ROOT_DIR}/Src/Module/LuaScript/LuaInterpreter
)

target_link_libraries(LuaConsole
	${ORBITER_LIB}
	${ORBITER_SDK_LIB}
	lua::lib
	${LUAINTERPRETER_LIB}
)

add_dependencies(LuaConsole
	${OrbiterTgt}
	Orbitersdk
	LuaInterpreter
)

set_target_properties(LuaConsole
	PROPERTIES
	FOLDER Modules
)

# Installation
install(TARGETS LuaConsole
	RUNTIME
	DESTINATION ${ORBITER_INSTALL_PLUGIN_DIR}
)
