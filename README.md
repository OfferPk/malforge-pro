# MALForge Pro (v1.0.0)

### CCSDS 521.0-B-2 & ISO 18445 Mission Operations Message Abstraction Layer (MAL) Studio

MALForge Pro is an aerospace-grade developer studio, interaction pattern state machine engine, message header codec, Common Object Model (COM CCSDS 522.0-B-1) service mapper, and 10-point normative compliance auditor designed for space mission software architects (NASA AMMOS, ESA SCOS-2000 / EGS-CC / Yamcs, JAXA, MBRSC UAE) and commercial NewSpace satellite operators.

---

## 🌟 Key Capabilities

- **6 Normative Interaction Patterns (CCSDS 521.0-B-2)**: Orchestrates full multi-stage state machines for SEND (1 stage), SUBMIT (2 stages), REQUEST (2 stages), INVOKE (3 stages), PROGRESS (4 stages), and PUBLISH-SUBSCRIBE (4 stages).  
- **Standard MAL Message Header Encoding**: Formats bit-exact headers with URI routing (`uriFrom`, `uriTo`), timestamps, 64-bit transaction correlation IDs, QoS levels (BESTEFFORT to ASSURED), priority, domains, and service keys.  
- **Common Object Model (COM) & M\&C Services**: Built-in support for Area 1 COM (Event, Archive) and Area 2 Monitor & Control (Action, Parameter, Alert) service interfaces.  
- **Standard Error Code & Semantics Handling**: Enforces normative error code allocation (\$65536 \\dots 65552\$) when the `isError` flag is active.  
- **Transaction Correlation Engine**: Maintains persistent transaction ID mapping across multi-stage interactions to prevent race conditions and cross-talk.  
- **10-Point Normative Compliance Auditor**: Automated verification engine enforcing rules `MAL-001` through `MAL-010`.

---

## 📂 Project Structure

mal-forge-pro/

├── source-code/

│   ├── mal-engine.js            \# Core MAL state machine, header codec & pattern sessions

│   ├── mal-auditor.js           \# 10-point normative compliance auditor

│   ├── mal\_cli.py               \# Pure Python 3 CLI executable

│   ├── mal-cli.py               \# Pure Python 3 CLI alias

│   ├── test\_runner.py          \# 10-suite unit test runner

│   └── index.html               \# Interactive Mission Control operations console

├── build/

│   └── mal-forge-pro-v1.0.0.zip \# Standalone production bundle

├── documentation/

│   ├── CCSDS\_MAL\_SPECIFICATION.md \# Normative protocol specification

│   └── MAL\_COMPLIANCE\_MATRIX.md   \# 10-point requirement traceability

└── screenshots/

    ├── architecture-diagram.svg  \# System architecture diagram

    └── mal-studio-preview.svg    \# Operations console preview

---

## 🚀 Quick Start

### Running Automated Tests

python3 source-code/test\_runner.py \-v

### Command Line Interface

\# Execute REQUEST interaction pattern session (2 stages: REQUEST \-\> RESPONSE)

python3 source-code/mal\_cli.py \--mode pattern \--pattern request

\# Execute INVOKE three-stage command sequence

python3 source-code/mal\_cli.py \--mode pattern \--pattern invoke \--payload "FIRE\_THRUSTER\_PULSE"

\# Generate standalone MAL message

python3 source-code/mal\_cli.py \--mode message \--payload "ATTITUDE\_TELEMETRY"

\# Run 10-Point Normative Compliance Audit

python3 source-code/mal\_cli.py \--mode audit

### Launching the Web Operations Console

Open `source-code/index.html` in any web browser to access the interactive Mission Control dashboard, interaction pattern sequence visualizer, PDU dissector, and 10-point compliance scorecard.