# Quantum Circuits (OPENQASM)

---

## Phi−

<button onclick="copyCode('phi_minus')">Copy</button>

```qasm
OPENQASM 2.0;
include "qelib1.inc";

qreg q[3];
creg c[3];

h q[0];
cx q[0], q[1];
z q[0];
```

---

## Phi+

<button onclick="copyCode('phi_plus')">Copy</button>

```qasm
OPENQASM 2.0;
include "qelib1.inc";

qreg q[3];
creg c[3];

h q[0];
cx q[0], q[1];
```

---

## Psi+

<button onclick="copyCode('psi_plus')">Copy</button>

```qasm
OPENQASM 2.0;
include "qelib1.inc";

qreg q[3];
creg c[3];

h q[0];
cx q[0], q[1];
x q[1];
```

---

## Psi−

<button onclick="copyCode('psi_minus')">Copy</button>

```qasm
OPENQASM 2.0;
include "qelib1.inc";

qreg q[3];
creg c[3];

h q[0];
cx q[0], q[1];
x q[1];
z q[0];
```

---

## GHZ

<button onclick="copyCode('ghz')">Copy</button>

```qasm
OPENQASM 2.0;
include "qelib1.inc";

qreg q[3];
creg c[3];

h q[0];
cx q[0], q[1];
cx q[1], q[2];
measure q -> c;
```

---

## Half Adder

<button onclick="copyCode('half_adder')">Copy</button>

```qasm
OPENQASM 2.0;
include "qelib1.inc";

qreg q[3];
creg c[2];

ccx q[0], q[1], q[2];
cx q[0], q[1];

measure q[1] -> c[0];
measure q[2] -> c[1];
```

---

## Full Adder

<button onclick="copyCode('full_adder')">Copy</button>

```qasm
OPENQASM 2.0;
include "qelib1.inc";

qreg q[4];
creg c[2];

ccx q[0], q[1], q[3];
cx  q[0], q[1];
ccx q[1], q[2], q[3];
cx  q[1], q[2];
cx  q[0], q[1];

measure q[2] -> c[0];
measure q[3] -> c[1];
```

---

# Toffoli Gate as Logic Gates

## AND

<button onclick="copyCode('toffoli_and')">Copy</button>

```qasm
OPENQASM 2.0;
include "qelib1.inc";

qreg q[3];  // q[0]=a, q[1]=b, q[2]=|0>
creg c[3];

ccx q[0], q[1], q[2];

measure q -> c;
```

---

## OR

<button onclick="copyCode('toffoli_or')">Copy</button>

```qasm
OPENQASM 2.0;
include "qelib1.inc";

qreg q[3];
creg c[3];

x q[0];
x q[1];
ccx q[0], q[1], q[2];
x q[2];
x q[0];
x q[1];

measure q -> c;
```

---

## NOT

<button onclick="copyCode('toffoli_not')">Copy</button>

```qasm
OPENQASM 2.0;
include "qelib1.inc";

qreg q[3];
creg c[3];

x q[0];
x q[1];
ccx q[0], q[1], q[2];

measure q -> c;
```

---

# Fredkin Gate as Logic Gates

## AND

<button onclick="copyCode('fredkin_and')">Copy</button>

```qasm
OPENQASM 2.0;
include "qelib1.inc";

qreg q[3];
creg c[3];

cswap q[0], q[1], q[2];

measure q -> c;
```

---

## NOT

<button onclick="copyCode('fredkin_not')">Copy</button>

```qasm
OPENQASM 2.0;
include "qelib1.inc";

qreg q[3];
creg c[3];

x q[2];
cswap q[0], q[1], q[2];

measure q -> c;
```

---
## OR

<button onclick="copyCode('fredkin_not')">Copy</button>

```qasm
OPENQASM 2.0;
include "qelib1.inc";

qreg q[3];
creg c[3];

x q[1];

cswap q[0], q[1], q[2];

measure q[0] -> c[0];  
measure q[1] -> c[1];  
measure q[2] -> c[2]; 

```

---

<script>
function copyCode(id) {
  const blocks = {
    phi_minus: `OPENQASM 2.0; ...`,
    phi_plus: `OPENQASM 2.0; ...`,
    psi_plus: `OPENQASM 2.0; ...`,
    psi_minus: `OPENQASM 2.0; ...`,
    ghz: `OPENQASM 2.0; ...`,
    half_adder: `OPENQASM 2.0; ...`,
    full_adder: `OPENQASM 2.0; ...`,

    toffoli_and: `OPENQASM 2.0;
include "qelib1.inc";
qreg q[3];
creg c[3];
ccx q[0], q[1], q[2];
measure q -> c;`,

    toffoli_or: `OPENQASM 2.0;
include "qelib1.inc";
qreg q[3];
creg c[3];
x q[0];
x q[1];
ccx q[0], q[1], q[2];
x q[2];
x q[0];
x q[1];
measure q -> c;`,

    toffoli_not: `OPENQASM 2.0;
include "qelib1.inc";
qreg q[3];
creg c[3];
x q[0];
x q[1];
ccx q[0], q[1], q[2];
measure q -> c;`,

    fredkin_and: `OPENQASM 2.0;
include "qelib1.inc";
qreg q[3];
creg c[3];
cswap q[0], q[1], q[2];
measure q -> c;`,

    fredkin_not: `OPENQASM 2.0;
include "qelib1.inc";
qreg q[3];
creg c[3];
x q[2];
cswap q[0], q[1], q[2];
measure q -> c;`
  };

  navigator.clipboard.writeText(blocks[id]);
  alert("Copied!");
}
</script>
