
| What you want to do                                       | Use                                                     | Example                            |
| --------------------------------------------------------- | ------------------------------------------------------- | ---------------------------------- |
| Connect wires directly                                    | `assign`                                                | `assign out = a & b;`              |
| Describe combinational logic (calculations, `if`, `case`) | `always_comb` (or `always @(*)`)                        | ALU, muxes, priority encoder       |
| Describe sequential logic (flip-flops/registers)          | `always_ff @(posedge clk)` (or `always @(posedge clk)`) | Counters, registers, FSM state     |
| Instantiate one or more modules                           | `generate` + `genvar`                                   | Ripple-carry adder, arrays of DFFs |

---

## 1. `assign` (Continuous assignment)

Use when it's just one expression.

```
assign out = a + b;
assign out = sel ? a : b;
assign out = a & b;
```

Think: **Connect wires together.**

---

## 2. `always_comb`

Use for combinational logic.

```
always_comb begin
    if (sel)
        out = a;
    else
        out = b;
end
```

```
always_comb begin
    case(op)
        2'b00: out = a+b;
        2'b01: out = a-b;
    endcase
end
```

Think: **Logic gates (no memory).**

---

## 3. `always_ff`

Use when a clock is involved.

```
always_ff @(posedge clk)
    q <= d;
```

Think: **Flip-flops/registers (has memory).**

---

## 4. `generate`

Use when creating multiple copies of hardware.

```
genvar i;
generate
    for(i=0;i<8;i++) begin
        full_adder fa(...);
    end
endgenerate
```

Think: **Duplicate hardware.**

---

# Decision tree

```
Need a clock?
│
├── Yes
│   └── always_ff
│
└── No
    │
    ├── Instantiating modules?
    │       └── generate + genvar
    │
    └── Just logic?
            │
            ├── One simple expression?
            │       └── assign
            │
            └── if / case / multiple statements?
                    └── always_comb
```

### Easy memory trick

- 📌 **`assign`** = **one equation**
- 📌 **`always_comb`** = **logic**
- 📌 **`always_ff`** = **memory**
- 📌 **`generate`** = **copy hardware**