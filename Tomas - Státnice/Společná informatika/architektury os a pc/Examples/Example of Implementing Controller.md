---
dg-publish: true
tags:
  - tomas
  - spolecna_informatika
  - architektura_pc_a_os
---
```python
# Not a real serial module implementation - this module mocks the serial module from pyserial package,
# but does not communicate with real RS-232 controller and is rather using simulated CPU commands to communicate
# with a simulated controller instead.

from datetime import timedelta
from datetime import datetime
import SimulatedCpuCommands as cpu

SEVENBITS = 7
STOPBITS_ONE = 1
PARITY_NONE = 0

def setSimulatedInputEvents(simulatedInputEvents):
    cpu.setSimulatedInputEvents(simulatedInputEvents)

class Serial:
    port = None

    def open(self):
        pass

    def read(self, bytesToReceive = 1):
        data = []
        lastByteTime = datetime.now()
        timeoutReached = False
        while bytesToReceive > 0:
            # Wait for a data byte
            statusByte = 0
            while statusByte == 0 and not timeoutReached:
                currentTime = datetime.now()
                if currentTime - lastByteTime > timedelta(seconds=self.timeout):
                    timeoutReached = True
                statusByte = cpu.readStatusRegister(self.port)
    
            if timeoutReached:
                break
            else:
                lastByteTime = currentTime

            # Save data byte into resulting variable
            dataByte = cpu.readDataRegister(self.port)
    
            data.append(dataByte)
            bytesToReceive -= 1
        return data

    def flushInput(self):
        pass

    def flushOutput(self):
        pass

    def setRTS(self, value):
        pass

    def setDTR(self, value):
        pass

    def close(self):
        pass

```
