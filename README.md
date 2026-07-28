# 🚀 Tiny RISC Processor – 5-Stage Pipeline (Verilog HDL)

A simple **32-bit Tiny RISC processor** developed in **Verilog HDL** using a **5-stage pipelined architecture**. This project is intended for learning processor design concepts, RTL development, and pipelined CPU implementation.

---

# 📖 Project Description

The processor is based on a traditional **Reduced Instruction Set Computer (RISC)** architecture with a fixed 32-bit instruction format. It employs a **five-stage instruction pipeline** to improve execution efficiency by processing multiple instructions simultaneously.

The pipeline consists of the following stages:

- **Instruction Fetch (IF)** – Reads instructions from instruction memory.
- **Instruction Decode (ID)** – Decodes instructions and accesses the register file.
- **Execute (EX)** – Performs arithmetic, logic, and address calculations.
- **Memory Access (MEM)** – Executes load and store operations.
- **Write Back (WB)** – Writes computation results back to the register file.

Dedicated **pipeline registers** are inserted between every stage to transfer data and control signals correctly.

---

# 🏛️ Processor Specifications

| Feature | Description |
|----------|-------------|
| Architecture | Tiny RISC |
| Pipeline Stages | 5 |
| Data Width | 32 Bits |
| Register File | 16 General-Purpose Registers (32-bit each) |
| Instruction Width | 32 Bits |
| RTL Style | Modular & Synthesizable |

---

# 📑 Instruction Encoding

Each instruction occupies **32 bits** and follows the format shown below.

```
 ---------------------------------------------------------
| Opcode | I | Destination | Source1 | Source2 | Immediate |
| 31:27  |26 |    25:22    | 21:18   | 17:14   |   13:0    |
 ---------------------------------------------------------
```

### Field Description

| Field | Function |
|--------|----------|
| `Opcode` | Selects the operation to execute |
| `I` | Indicates immediate-mode instruction |
| `rd` | Destination register |
| `rs1` | First source register |
| `rs2` | Second source register |
| `Immediate` | 14-bit signed immediate value |

The immediate operand is sign-extended before being processed by the ALU.

---

# 🧮 Supported Operations

| Opcode | Operation | Description |
|:------:|-----------|-------------|
| 00000 | ADD | Integer Addition |
| 00001 | SUB | Integer Subtraction |
| 00010 | AND | Logical AND |
| 00011 | OR | Logical OR |
| 00100 | XOR | Logical XOR |
| 00101 | MOV | Move / Load Immediate |
| 00110 | MUL | Multiplication |
| 00111 | DIV | Division |
| 01000 | LOAD | Read data from memory |
| 01001 | STORE | Write data to memory |

Both **register-based** and **immediate-mode** instructions are supported through the immediate control flag.

---

# ⚙️ Control Unit and Datapath

The processor includes a dedicated control unit responsible for producing the required control signals during instruction execution.

### Generated Control Signals

- `regwrite`
- `memwrite`
- `memtoreg`
- `alusrc`
- `aluop`

To ensure proper synchronization, all control signals are transferred through the corresponding pipeline registers. Immediate operands are sign-extended before entering the execution stage.

---

# 🧪 Functional Verification

The processor has been verified using a dedicated Verilog testbench.

Verification includes:

- Preloaded instruction memory
- Execution of sample instruction sequences
- Validation of register contents after simulation
- Waveform analysis for pipeline operation

*(Insert simulation waveform or screenshot here if available.)*

---

# 📂 Project Modules

| Module | Function |
|----------|----------|
| `instruction_mem` | Stores program instructions |
| `if_id` | IF/ID pipeline register |
| `decode` | Instruction decoder |
| `id_ex` | ID/EX pipeline register |
| `control_unit` | Generates processor control signals |
| `register_file` | General-purpose register bank |
| `op` | Operand selection multiplexer |
| `alu` | Arithmetic Logic Unit |
| `ex_mem` | EX/MEM pipeline register |
| `mem_stage` | Data memory interface |
| `mem_wb` | MEM/WB pipeline register |
| `write_back` | Register write-back stage |
| `risc` | Top-level processor module |

---

# 🚀 Future Enhancements

Possible improvements include:

- Data forwarding (bypassing) unit
- Hazard detection logic
- Branch and jump instruction support
- Pipeline stalling mechanism
- Pipeline flushing logic
- Performance optimization

---

# 🎓 Learning Objectives

This project helps in understanding:

- Five-stage pipelined processor architecture
- Pipeline register implementation
- Processor control signal generation
- Datapath organization
- RTL coding techniques in Verilog
- Fundamental concepts of CPU microarchitecture

---

# 👨‍💻 Developer

**Rahul Rathlavath**

**Area of Interest:** RTL Design • VLSI • Digital Design • Computer Architecture
