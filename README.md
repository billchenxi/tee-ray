<p align="center">
  <img src="assets/tee_ray_logo.png" alt="TEE-Ray Logo" width="220">
</p>

# tee-ray

TEE-Ray is a Ray-compatible secure orchestration layer that routes distributed
ML tasks and data access through Trusted Execution Environments (TEEs). It adds
encrypted payloads, TEE-backed data storage, attestation-aware scheduling,
secure logging, and pluggable TEE backends for private training and inference.

## Status

🚧 Early prototype / research phase – APIs may change.

## Install (dev)

```bash
pip install -e .
```

## Repo structure
```
tee-ray/
├─ README.md
├─ pyproject.toml          # or setup.cfg / setup.py
├─ .gitignore
├─ tee_ray/
│  ├─ __init__.py
│  ├─ config.py
│  ├─ tee/
│  │  ├─ __init__.py
│  │  ├─ base.py          # abstract TEE interface
│  │  ├─ mock_tee.py      # local dev fake-TEE
│  │  └─ nitro_tee.py     # real impl later
│  ├─ ray_integration/
│  │  ├─ __init__.py
│  │  ├─ secure_cluster.py  # start/attach Ray with TEE policies
│  │  └─ secure_tasks.py    # decorators / helpers
│  ├─ logging/
│  │  ├─ __init__.py
│  │  └─ secure_logger.py   # encrypted/log-sanitizing logger
│  └─ examples/
│     ├─ simple_task.py
│     └─ mnist_training.py
├─ scripts/
│  ├─ run_simple_local.sh
│  └─ start_mock_cluster.sh
├─ docker/
│  ├─ Dockerfile.mock
│  └─ Dockerfile.nitro     # later
└─ tests/
   ├─ test_mock_tee.py
   └─ test_secure_tasks.py
```
