MuteX is a Windows console application written in C# designed for managing system-wide named mutex objects and performing payload configuration decoding. It provides an interactive command-line environment for acquiring, inspecting, and releasing synchronization primitives in real-time.System RequirementsWindows OS.NET Framework 4.0 or higher (uses csc.exe for compilation)CompilationTo compile the application using standard .NET command-line tools:build.bat
This invokes the C# compiler and produces MuteX.exe.Architecture & FeaturesInteractive Command Environment: Custom REPL shell (MuteX\root>) supporting dynamic input execution.Mutex Management: Synchronous and asynchronous acquisition of system-level named mutexes using System.Threading.Mutex.Session Tracking: Internal state dictionary tracks held handle references for targeted or batch releases upon shell termination.Payload Decoder: Decodes Base64 UTF-8 encoded configuration strings inline.Command ReferenceExecute !menu inside the interactive shell to display available operational commands.CommandArgumentsDescription!menuNoneDisplays command syntax and operational reference.hold<MutexName>Attempts creation or ownership acquisition of a named system mutex.check<MutexName>Queries the system for existence of a specified named mutex handle.release<MutexName>Releases ownership and disposes of a specific session-managed mutex.releaseallNoneReleases and disposes of all mutex handles managed by the active session.listNoneOutputs all active mutex handles currently owned by the session process.decode<Base64String>Decodes UTF-8 string values from standard Base64 encoding.cls / clearNoneClears the active console window.exitNoneExecutes batch mutex cleanup and closes the process shell.Usage ExamplesBase64 String DecodingMuteX\root> decode VGVzdGluZ011dGVY
[ + ] Decoded: TestingMuteX
Mutex Acquisition and VerificationMuteX\root> hold Global\SystemLock_01
[ + ] Mutex successfully created & held: Global\SystemLock_01

MuteX\root> check Global\SystemLock_01
[ + ] Mutex 'Global\SystemLock_01' EXISTS.

MuteX\root> list
--- [ ACTIVE MUTEXES (1) ] ---
  -> Global\SystemLock_01
------------------------------------

MuteX\root> release Global\SystemLock_01
[ + ] Released: Global\SystemLock_01
License and NoteDeveloped for system utility testing, thread synchronization inspection, and environment analysis on Windows operating systems.
