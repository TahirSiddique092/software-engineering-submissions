# Lab 7: Fuzzing for Input Validation Bugs

**Name:** Mohammed Tahir Siddique | **SRN:** PES2UG24AM092

This lab was completed in a separate repository, forked from the lab's starter repository. Labs 6 and 7 share that repository.

**Submission repository:** https://github.com/TahirSiddique092/L6_L7_13_pet_walking_service (folder `Lab 7`)

The buggy `processor.py` was fuzz tested with Hypothesis, and the input validation bugs it exposed were fixed.

| Deliverable | File in the submission repository |
|-------------|-----------------------------------|
| PDF document with the screenshots | [Lab7_Screenshots_PES2UG24AM092.pdf](https://github.com/TahirSiddique092/L6_L7_13_pet_walking_service/blob/main/Lab%207/Lab7_Screenshots_PES2UG24AM092.pdf) |
| Fixed application script | [processor.py](https://github.com/TahirSiddique092/L6_L7_13_pet_walking_service/blob/main/Lab%207/processor.py) |
| Updated fuzz tests | [test_processor.py](https://github.com/TahirSiddique092/L6_L7_13_pet_walking_service/blob/main/Lab%207/test_processor.py) |

| Run | Result |
|-----|--------|
| Fuzz tests against the buggy code | 7 failed, 2 passed |
| Fuzz tests against the fixed code | 9 passed |

Forked from: https://github.com/SETAPESU26/L6_L7_13_pet_walking_service
