#---
#
# Copyright (c) 2019 Evandro de Souza
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License version 2 as
# published by the Free Software Foundation;
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA
#
# Author:  Evandro de Souza <evandro@ualberta.ca>
# Date:    2019.08.14
# Company: University of Alberta/Canada - Computing Science
#
#---



#-----------------------------------------------------------------------------#
#   Main Variables                                                            #
#-----------------------------------------------------------------------------#

BASE_DIR   := .
PRJ        := NS3MosaikSim

PRJ_DIR     = ${BASE_DIR}/mosaik_api
OBJ_DIR     = ${PRJ_DIR}/obj
SRC_DIR	    = ${PRJ_DIR}/src
INC_DIR	    = ${PRJ_DIR}/include

NS3_ROOT    = ../ns-allinone-3.33/ns-3.33
NS3_INC     = ${NS3_ROOT}/build
NS3_LIB     = ${NS3_ROOT}/build/lib

CX=g++
RM=/bin/rm



#----------------
#--- Includes ---
#----------------
INCLUDES =	-I${INC_DIR}\
		    -I${NS3_INC}


#---------------
#--- CXFLAGS ---
#---------------
#CXFLAGS  = -c -Wall -Wextra  -std=c++11 -O0
CXFLAGS  = -c -std=c++14 -O3
CXFLAGS +=


#---------------
#--- LXFLAGS ---
#---------------
LXFLAGS = -ljsoncpp\
          ${NS3_LIB}/libns3.33-core-optimized.so\
          ${NS3_LIB}/libns3.33-internet-optimized.so\
          ${NS3_LIB}/libns3.33-applications-optimized.so\
          ${NS3_LIB}/libns3.33-network-optimized.so\
          ${NS3_LIB}/libns3.33-point-to-point-optimized.so\
          ${NS3_LIB}/libns3.33-mobility-optimized.so\
          ${NS3_LIB}/libns3.33-bridge-optimized.so\
          ${NS3_LIB}/libns3.33-traffic-control-optimized.so\
          ${NS3_LIB}/libns3.33-stats-optimized.so\
		  ${NS3_LIB}/libns3.33-csma-optimized.so\
#          ${NS3_LIB}/libns3.33-mpi-optimized.so\


# LXFLAGS = -ljsoncpp\
#          ${NS3_LIB}/libns3.33-core-debug.so\
#          ${NS3_LIB}/libns3.33-internet-debug.so\
#          ${NS3_LIB}/libns3.33-applications-debug.so\
#          ${NS3_LIB}/libns3.33-network-debug.so\
#          ${NS3_LIB}/libns3.33-point-to-point-debug.so\
#          ${NS3_LIB}/libns3.33-mobility-debug.so\
#          ${NS3_LIB}/libns3.33-bridge-debug.so\
#          ${NS3_LIB}/libns3.33-traffic-control-debug.so\
#          ${NS3_LIB}/libns3.33-stats-debug.so\
# 		 ${NS3_LIB}/libns3.33-csma-debug.so\
#          ${NS3_LIB}/libns3.33-mpi-debug.so\


#------------------------#
#--- Print Debug Info ---#
#------------------------#
# $(info $$PRJ_DIR is [${PRJ_DIR}])
# $(info $$OBJ_DIR is [${OBJ_DIR}])
# $(info $$SRC_DIR is [${SRC_DIR}])
# $(info $$NS3_INC is [${NS3_INC}])
# $(info $$NS3_LIB is [${NS3_LIB}])
# $(info $$INCLUDES is [${INCLUDES}])
# $(info $$CX_OBJ_FILES is [${CX_OBJ_FILES}])
# $(info $$LXFLAGS is [${LXFLAGS}])



#--------------------#
#--- Main Project ---#
#--------------------#
$(PRJ):	$(OBJ_DIR)/main.o $(OBJ_DIR)/ns3-helper.o $(OBJ_DIR)/NS3Netsim.o $(OBJ_DIR)/MosaikSim.o
	$(CX) -lm -o $@ $^ $(LXFLAGS)

$(OBJ_DIR)/main.o: ${SRC_DIR}/main.cpp | $(OBJ_DIR)
	$(CX) $(CXFLAGS) $(INCLUDES) -c $^ -o $@

$(OBJ_DIR)/NS3Netsim.o: ${SRC_DIR}/NS3Netsim.cpp
	$(CX) $(CXFLAGS) $(INCLUDES) -c $^ -o $@

$(OBJ_DIR)/MosaikSim.o: ${SRC_DIR}/MosaikSim.cpp
	$(CX) $(CXFLAGS) $(INCLUDES) -c $^ -o $@

$(OBJ_DIR)/ns3-helper.o: ${SRC_DIR}/ns3-helper.cpp
	$(CX) $(CXFLAGS) $(INCLUDES) -c $^ -o $@

$(OBJ_DIR):
	mkdir -p $@

.PHONY: clean
clean:
	$(RM) -f $(PRJ_DIR)/obj/$(PRJ).o \
	$(PRJ_DIR)/obj/main.o  \
	$(PRJ_DIR)/obj/MosaikSim.o \
	$(PRJ_DIR)/obj/NS3Netsim.o \
	$(PRJ_DIR)/obj/ns3-helper.o  \
	$(PRJ)
