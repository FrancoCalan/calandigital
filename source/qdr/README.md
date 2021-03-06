Here lies the ROACH2 QDR calibration software.

Based on work by SKA-SA, a few tweaks have been added to provide (hopefully)
reliable calibration an any feasible QDR clock speed.

To use the software do the following:

```python
#########################################
import qdr


# Instantiate a qdr.
# The first argument should be an FpgaClient instance
# The second argument refers to the name of the qdr you wish to calibrate

my_qdr = qdr.Qdr(r, 'qdr0')

# Calibrate!
# The calibration will read and write data to the top half of the
# QDR address space. If your firmware design is using this space,
# you'll need to disable the FPGA-side write interface, or else
# it will interfere with the calibration routine.

# "fail_hard" will cause an error if calibration fails.
# "verbosity" controls the amount of information printed to screen.
# >1 is probably only desirable for debug.

my_qdr.qdr_cal(fail_hard=True, verbosity=1) 
```

### calandigital Notes
To use this package with calandigital some lines change:

```python
import calandigital as cd
my_qdr = cd.Qdr(r, 'qdr0')
```

The rest is the same.
