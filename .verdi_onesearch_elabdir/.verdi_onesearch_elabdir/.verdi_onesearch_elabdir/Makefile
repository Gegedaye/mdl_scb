test = my_case1
seed = 1
verbosity = UVM_MEDIUM
FILES = top_tb.sv my_env.sv my_model.sv my_scoreboard.sv my_transaction.sv my_agent.sv my_driver.sv my_if.sv my_monitor.sv my_sequencer.sv base_test.sv my_case0.sv my_case1.sv dut/dut.sv 
FLAGS = -full64 -sverilog -debug_access+all -timescale=1ns/10ps -ntb_opts uvm-1.2  -lca -kdb -l comp.log

run:	simv
	./simv -l simv.log +ntb_random_seed=${seed} +vpdfile+./1.vpd +fsdbfile+./1.fsdb  +UVM_TESTNAME=${test}

random:	simv
	./simv -l simv.log +ntb_random_seed_automatic +vpdfile+./1.vpd +fsdbfile+./1.fsdb  +UVM_TESTNAME=${test} +UVM_VERBOSITY=${verbosity}

gui:	simv
	./simv -gui  

simv:	${FILES}
	vcs ${FLAGS} ${FILES}


DIR = $(shell basename `pwd`)
tar:	clean
	cd ..;tar cvf ${DIR}.tar ${DIR}

clean: 	
	@rm -rf csrc simv* *.tcl *.vpd *.fsdb .res* ucli* .ucli* *.old *.txt *.db 
	@rm -rf *.log DVEfiles verdiLog vc_hdrs.h novas*
