# 10. I/O and Device Management

## What is I/O?
I/O means **Input/Output**:
- Input: keyboard, mouse, camera, microphone, sensors.
- Output: display, speaker, printer, actuator.
- Storage/network devices can perform both input and output.

The OS coordinates access to devices and provides common interfaces to applications.

## Device driver
A driver is software that helps the OS communicate with a particular device or device class. A driver handles device-specific details so applications do not each need to implement them.

## General device interaction flow
```text
Application
   |
   v
OS API / system service
   |
   v
Kernel and device driver
   |
   v
Device controller / hardware
   |
   v
Data or completion status returns
   |
   v
OS notifies or resumes application
```
Exact details vary by operating system and device.

## Example: Keyboard input
1. You press a key.
2. Keyboard hardware/controller reports input.
3. The OS input stack and driver process the event.
4. The OS routes the input to the appropriate application/window.
5. The application updates the screen.

## Example: Camera capture
1. App requests camera access.
2. OS checks permissions and manages camera ownership/session.
3. Camera framework/driver configures the device.
4. Hardware produces image data.
5. App receives frames and processes them.
6. File/storage services help save a photo if requested.

## Interrupts
An **interrupt** alerts the CPU that an event needs attention, such as device completion. The OS handles the event and may schedule further work.

## Polling vs interrupts
- **Polling:** software repeatedly checks whether a device/event is ready.
- **Interrupt-driven:** device/controller signals when attention is needed.
Polling can be simple but waste CPU time if used excessively. Interrupts reduce repeated checking but require event-handling overhead.

## DMA — Direct Memory Access
DMA allows a capable device/controller to transfer data to or from memory with less CPU involvement in copying each unit. The CPU and OS still configure and coordinate the transfer, and completion may be signaled with an interrupt.

## Buffering and spooling
- **Buffering:** temporarily stores data during transfer.
- **Spooling:** queues jobs for a device that processes them serially, such as a printer queue.

## Device management responsibilities
- Track device state and access.
- Coordinate drivers.
- Handle errors and completion notifications.
- Manage queues and buffering.
- Enforce permissions and resource sharing.
