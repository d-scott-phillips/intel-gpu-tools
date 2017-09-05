tools_progs_noisnt = [
	'hsw_compute_wrpll',
	'skl_compute_wrpll',
	'skl_ddb_allocation',
]

foreach prog : tools_progs_noisnt
	executable(prog, prog + '.c',
			dependencies : igt_deps,
			install : false)
endforeach

tools_progs = [
	# FIXME we already have a libtestcase with this name as target
	#'igt_stats',
	'intel_audio_dump',
	'intel_backlight',
	'intel_bios_dumper',
	'intel_display_crc',
	'intel_display_poller',
	'intel_forcewaked',
	'intel_gpu_frequency',
	'intel_firmware_decode',
	'intel_gpu_time',
	'intel_gpu_top',
	'intel_gtt',
	'intel_guc_logger',
	'intel_infoframes',
	'intel_lid',
	'intel_opregion_decode',
	'intel_panel_fitter',
	'intel_reg_checker',
	'intel_residency',
	'intel_stepping',
	'intel_vbt_decode',
	'intel_watermark',
	'intel_gem_info',
	'intel_gvtg_test',
]
tool_deps = igt_deps

if libdrm_intel.found()
	tools_progs += [
		'intel_dump_decode',
		'intel_error_decode',
		'intel_framebuffer_dump',
		'intel_perf_counters',
	]
	tool_deps += zlib
endif

foreach prog : tools_progs
	executable(prog, prog + '.c',
			dependencies : tool_deps)
endforeach

shared_library('intel_aubdump', 'aubdump.c', dependencies : [ igt_deps, dlsym ])

subdir('null_state_gen')