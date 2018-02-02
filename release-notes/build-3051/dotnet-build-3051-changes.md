# .NET Framework Build 3051 Release Notes

.NET Framework release notes describe product improvements grouped by product area. Each change includes a Microsoft-internal VSTS bug ID, the primary binary that was updated and whether the change was a bug or a feature.

## ASPNET 
* Support for Dependency Injection in Page, Custom Handler and User controls. [364308, system.web.dll, Feature]
* Enable ASP.NET developers to specify MaxLength attribute for Multiline asp:TextBox. [449020, System.Web.dll, Bug]
* Avoid InvalidCastException when running an ASP.NET application that works with mixed HttpWorkerRequests types and has FREB/ETW tracing enabled. [472566, system.web.dll, Bug]
* Fixed issue https://github.com/Microsoft/dotnet-framework-early-access/issues/2 [479409, 521834, system.web.dll, Bug]
* With this improvement, users who created apps on .NET Framework 4.7.2+ or upgraded apps to .NET Framework 4.7.2+, if they don't specify the appsetting value in their configurations, they won't be using regexes in data type attributes (such as EmailAddressAttribute, UrlAttribute, and PhoneAttribute). They will instead use a simpler implementation. [480141, system.web.dll, Bug]
* Support for SameSite property in HttpCookie. [497045, system.web.dll, Feature]
* Fixed bug in ASP.NET LowPhysicalMemoryMonitor where the monitor might fail to start if memory use falls within a certain range. [531575, system.web.dll, Bug]
* Fixed bug in ASP.NET LowPhysicalMemoryMonitor where the default polling interval is sometimes mistakenly disabled. [531576, system.web.dll, Bug]
* Fixed the behavior of ASP.NET's RecycleLimitMonitor in cases where no private bytes recycling limit is explicitly set in IIS configuration. [531579, system.web.dll, Bug]

## BCL 
* Increased throughput of decompression zip archives by ~3x. [199232, mscorlib.dll, Feature]
* Reduction in HashSet<T> memory consumption via StructLayout. [212195, mscorlib.dll, Bug]
* Added ConcurrentDictionary GetOrAdd/AddOrUpdate overloads with generic argument. [212212, 515491, mscorlib.dll, Bug]
* Improvement in performance of ConcurrentDictionary. [212582, mscorlib.dll, Bug]
* Performance improvements for HashSet construction from another HashSet. [212624, mscorlib.dll, Bug]
* Added HashSet<T> ctors with capacity. [212788, mscorlib.dll, Feature]
* Added ConcurrentDictionary GetOrAdd/AddOrUpdate overloads with generic argument. [212820, mscorlib.dll, Feature]
* Support for additional DSA factory methods to make key creation easier. [221261, mscorlib.dll, Feature]
* Support for additional RSA factory methods to make key creation easier. [223399, mscorlib.dll, Feature]
* Improved reliability when working with large expression trees. [256966, system.core.dll, Bug]
* Support for loading certificate PFX files without writing the private key to the hard drive. [258543, mscorlib.dll, Feature]
* Added a leaveOpen constructor on CryptoStream to mitigate problems with disposing the CryptoStream that ends up disposing the underlying stream which is not desirable in certain scenarios. [272215, mscorlib.dll, Bug]
* Support for SHA-2 hash algorithms in Rfc2898DeriveBytes. [272906, mscorlib.dll, Feature]
* Implement Enumerable.ToHashSet. [291752, system.core.dll, Feature]
* Added TryGetValue method to HashSet. [381763, system.core.dll, Feature]
* Fixed a problem where using OnDeserilalizingAttribute/OnDeserializedAttribute/OnSerializingAttribute/OnSerializedAttribute in a type in an assembly targeting NetStandard 2.0 would throw a TypeLoadException when accessing the type. [407239, mscorlib.dll, Bug]
* Support for programmatically creating X.509 certificates and certificate signing requests. [428598, mscorlib.dll, Feature]
* Fixed a problem where EventSource logging to ETW can fail in 32-bit large address aware processes. [443469, system.dll, Bug]
* Fixed security vulnerability tracked by Microsoft Common Vulnerabilities and Exposures CVE-2018-0764. [455812, 507252, system.xml.dll, Bug]
* Fixed a problem in returning Byte-Order-Mark with UTF8 objects when the default codepage on Windows is set to UTF8 codepage (65001) in Encoding.Default. Applications run into problems in this scenario and the Byte-Order-Mark is no longer sent with the UTF8 objects.  [460626, mscorlib.dll, Bug]
* ReaderWriterLockSlim now scales better under contention. See https://github.com/dotnet/coreclr/pull/13495 and https://github.com/dotnet/coreclr/pull/13243 for more details. [468648, mscorlib.dll, Bug]
* File and directory enumeration performance is now improved. Enumerating will be faster and allocate significantly less than before. [470762, mscorlib.dll, Bug]
* Increment the assembly version of System.Net.Http and System.IO.Compression to be compatible with netstandard 2.0 and the compatibility package. [504519, mscorlib.dll, Feature]
* Fixed problem where in certain scenarios corrupted zip is produced. [504526, mscorlib.dll, Bug]
* Avoid allocations in DateTime.Now [504528, mscorlib.dll, Bug]
* Make Lazy initialization of TextInfo.IsAsciiCasingSameAsInvariant thread safe. [504530, mscorlib.dll, Bug]
* Use beforefieldinit field for Comparer/EqualityComparer.Default. [504531, mscorlib.dll, Bug]
* Avoid duplicated computations with DateTime.GetDatePart. [504571, mscorlib.dll, Bug]
* Peformance of Buffer.MemoryCopy was significantly improved for smaller buffers. [504573, mscorlib.dll, Bug]
* Improve string.Equals OrdinalIgnoreCase performance for matching chars. [504580, mscorlib.dll, Bug]
* Avoid duplicated computations with DateTime.GetDatePart. [504591, 504571, BCL, Bug]
* Make GetProcessInfo() for a single PID cheaper on Windows. [505023, mscorlib.dll, Bug]
* Support for netstandard runtime facade type forward to contracts when possible, to enable usage of OOB types that were moved inbox on a .NET Framework 4.6.1 app that tries to run on .NET Framework 4.7.1+. [510901, mscorlib.dll, Bug]
* Support for compatibility with the support package, so that running netstandard apps on .NET Framework 4.7.1 is possible. [514195, mscorlib.dll, Bug]
* Support for ConcurrentDictionary GetOrAdd/AddOrUpdate overloads with generic argument. [515491, mscorlib.dll, Bug]
* Support for ephemeral asymmetric keys to be consistently exportable. [516638, mscorlib.dll, Bug]
* Exposed the signature algorithm identifier and the signature value on CMS SignerInfo. [517223, mscorlib.dll, Feature]
* Performance improvement of ManualResetEventSlim under contention. [517311, mscorlib.dll, Bug]
* Fixed managed attributes for assemblies System.Diagnostics.Tracing.dll, System.IO.Compression.dll, and System.Net.Http.dll. [522034, System.dll, Bug]
* Enable CodeDOM to generate trusted code when Device Guard by maintaining integrity of inputs and outputs. [526489, mscorlib.dll, Feature]
* Fixed problem with RuntimeInformation static class to now return the right value for architecture. [534300, mscorlib.dll, Bug]

## CLR
* Reliably handle scenarios where framework assemblies are present in DEVPATH. [207947, clr.dll, Bug]
* The GC will now compact the heap more aggressively when running out of virtual address space in 32-bit processes, even if there is a great deal of physical memory available on the machine. [377888, clr.dll, Bug]
* Fixed hang when loading NI images whose IL assemblies are not in the GAC, where the NI images have circular dependencies and COMPlus_NgenBind_OptimizeNonGac is enabled. [452001, clr.dll, Bug]
* Fixed a silent bad codegen bug. [467692, clrjit.dll, Bug]
* Improved reliability in a scenario with certain mixtures of LOH heap expansion and background GC operation. [470006, clr.dll, Bug]
* This fixes a bad error message with truncated type names when running TlbExp.exe with /verbose, or using ITypeLibExporterNotifySink.ReportEvent API. [480497, Tlbexp.exe, Bug]
* Fixed a problem where the GC can crash when recovering from an out-of-memory exception when performing a GC. [487315, clr.dll, Bug]
* Fixed problem where certain multithreaded programs can experience extremely intermittent crashes, normally during program startup. [490377, clr.dll, Bug]
* Fixed unpredictable crashes that can occur when trying to read custom attributes from assemblies carrying an invalid metadata pattern emitted by certain pre-v2 compilers. [497461, clr.dll, Bug]
* Fixed hang when loading NI images whose IL assemblies are not in the GAC, where the NI images have circular dependencies and COMPlus_NgenBind_OptimizeNonGac is enabled. [509957, clr.dll, Bug]
* Fixed a potential deadlock in ReadyToRun scenarios in cases where exception handling and code heap modification occur simultaneously. [510081, clrjit.dll, Bug]
* Fixed a floating-point overflow in the thread pool’s hill climbing algorithm. [511559, clr.dll, Bug]
* Hardens .NET library loading security if an administrator opts into the new Device Guard Dynamic Code Security policy. [517453, clr.dll, Bug]
* Fixed a problem where a SetConsoleCtrlHandler function is not executed during debugging when Visual Studio is set to not handle Ctrl+C events. [518982, system.dll, Bug]
* This change adds a dynamic method unload event that is fired whenever a dynamic method is destroyed. This is needed because profilers can listen to dynamic method load events (via DynamicMethodJittingStarted/Finished) but previously would never be notified of destroyed dynamic methods. This can happen for example when the dynamic method is garbage collected.  [523635, CorGuids.lib, Feature]
* Improved reliability of jump stub allocation. Corresponding .NET Core change: https://github.com/dotnet/coreclr/pull/15296 [537668, clr.dll, Bug]

## ClickOnce
* Fixed validation of SHA2 certificates for ClickOnce applications to allow avoiding SmartScreen for trusted publishers. This also allows customers to block installation of unsigned ClickOnce applications. [395008, system.deployment.dll, Bug]
* With this improvement, WPF developers can set a non-default DPI Awareness mode in their application manifest to take advantage of recent OS improvements in HDPI while still able to deploy via ClickOnce. [480091, Dfshim.dll, Feature]
* Support for timestamping ClickOnce manifest using RFC3161 timestamp servers. [480646, mage.exe, Feature]
* The value of the progress bar in the ClickOnce installation progress window is now read correctly by the Narrator. The decorative dividers of the ClickOnce installation progress window are no longer read by the Narrator. [526717, dfsvc.exe, Bug]
* ClickOnce app install and app launch windows are now accessible for the Narrator users [523737, dfsvc.exe, Bug]

## Networking
* Improved reliability by correctly processing Unicode characters in file URIs that point to UNC shares. [95292, System.dll, Bug]
* Fixed a reliability problem with how IPV6 Addresses are converted to strings after their scope ID has been modified. [95508, System.dll, Bug]
* Improved reliability in the scenario where HttpClientHandler.SendAsync functions as expected even when started in a task with a custom TaskScheduler. [110673, System.dll, Bug]
* Fixed HttpClient so that OperationCanceledException/TaskCanceledException's being returned from canceled requests will now have the proper settings on the Exception.CancellationToken property. [111275, System.dll, Bug]
* Fixed argument validation of System.Net.Mime.HeaderCollection Set/Add methods, and correct parameter name in exception message. [116743, System.dll, Bug]
* Fixed Socket ReceiveAsync to use the specified output buffers when receiving data extremely quickly over TCP and using several different sized buffers. [119549, System.dll, Bug]
* Fixed a problem in System.Uri where Unicode bidirectional control characters would be stripped from a Uri during parsing. This behavior change can be disabled by setting the new App Context Switch Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters. [130850, System.dll, Bug]
* Fixed parsing of ‘Set-Cookie’ headers received with Http APIs (HttpWebRequest, WebClient, HttpClient) for CookieContainer so that all valid cookies are correctly stored in the CookieContainer. [143892, System.dll, Bug]
* Fixed a problem with System.Uri to ensure that URI reserved character decoding behavior strictly conforms to the RFC 3986 specification. This means that the percent encoded versions of " : ", " ' ", " ( ",  " ) ", " ! " and " * " will no longer be incorrectly decoded when generating the absolute URI. [150266, System.dll, Bug]
* Use a global lock to protect AddressChangeListener and AvailabilityChangeListener states from race conditions. [162830, System.dll, Bug]
* Socket.BeginConnect will now consistently throw InvalidOperationException when attempting multiple operations. [188428, System.dll, Bug]
* Improved reliability by ensuring that URIs with unknown schemes and no host are normalized correctly and the URI path is processed correctly.  [233623, System.dll, Bug]
* Fixed the System.Net.Http.Headers.ContentDispositionHeaderValue class so that setting the Size property no longer throws a NullReferenceException. [251481, System.dll, Bug]
* Fixed a problem by preventing System.Uri.TryCreate from throwing a NullReferenceException when creating a relative URI that contains Unicode characters. [287019, System.dll, Bug]
* Fixed a reliability issue with HttpWebRequest so that closed connections can be correctly removed from the connection pool and additional requests sent correctly. [371763, System.dll, Bug]
* Added implementation to HttpClientHandler so that the newly added properties in .NET Framework 4.7.1 will no longer throw PlatformNotSupportedException. [386926, System.dll, Feature]
* Fixed ServicePoint.CloseConnectionGroup() so that it properly closes all connections associated with the connection group name passed in the method parameter. [404684, System.dll, Bug]
* Fixed the System.Net.WebHeaderCollection.GetValues() method to properly return cookies that have an 'Expires' attribute. [467951, System.dll, Bug]
* Fixed System.Net HTTP APIs (WebClient, HttpWebRequest, HttpClient) so that connections to the proxy to set up the CONNECT tunnel (for TLS/SSL requests) will now have the 'User-Agent' header passed to the request if that header was added by the developer to the original http request. [486995, System.dll, Bug]
* Fixed a reliability issue with HttpWebRequest and HttpClient where socket connection errors would prevent Http requests from being retried automatically. [493616, System.dll, Bug]
* Fixed SmtpClient so that it can properly send mail to SMTP servers that use the Kerberos protocol via GSSAPI for authentication. [495813, System.dll, Bug]
* Eliminate a deadlock situation when closing WebSocket connections. [497690, System.dll, Bug]
* Fixed a problem with AppContext switch Switch.System.Net.DontEnableSchSendAuxRecord where it failed to properly allow for the switch to be enabled. [511005, System.dll, Bug]
* Fixed a problem with connection limit when using HttpClient to send requests to loopback addresses. More info: https://github.com/Microsoft/dotnet/blob/master/releases/net471/KnownIssues/534719-Networking%20ServicePoint.ConnectionLimit%20default%20behavior%20with%20loopback%20changed%20unexpectedly.md. [534719, System.dll, Bug]

## SQL
* While receiving XEvents using SqlClient, the last XEvent was not retrieved unless the server pushed more data down to the client. This bug is fixed. All XEvents will not be instantly available. [104572, System.Data.dll, Bug]
* Fixed the DataSet memory leak issue in System.data.dll.  Datatable constraint’s Dataset field will be equal to Datatable’s Dataset field once Datatable’s DataSet is modified. [404667, System.Data.dll, Bug]
* SQL Azure can now support failover-partner when connecting to GeoDr database using readonly application intent, failover partner is one secondary DB replica specified by SQLAzure during the login time. [479724, System.Data.dll, Feature]
* With this new improvement, customers can use functionality introduced as a part of Always Encrypted v2. [481138, System.Data.dll, Feature]
* With this fix, SqlBulkCopy can be performed without the issue caused when SqlDecimal 0 is inserted to a table column which type has the same precision size as its scales size. It prevents the SqlBulkCopy error caused when a SqlDecimal value having larger precision than its minimum precision is inserted to a table column, which the SqlDecimal value can be adjusted to fit the column type. [481988, System.Data.dll, Bug]
* Added a new value for the SQL connection string keyword.  [484823, System.Data.dll, Feature]
* This prevents potential Connection Pool fragmentation and increases the performance of connection opening. [489852, System.Data.dll, Bug]
* This prevents connection hang that happens when users try to connect to mirrored SQL Server with timeout set to 0.  [498136, System.Data.dll, Bug]
* This change adds a try-finally wrapper around AbortTransaction() calls in SqlBulkCopy. WriteRowSourceToServerAsync(). The finally block ensures a lock is properly released in case AbortTransaction throws an exception due to a closed underlying connection. Not releasing the lock can lead to hangs later on in SqlConnection.Dispose() and Close(). [499706, System.Data.dll, Bug]
* Fixed failure to get return value from stored procedure in SQL Server when the return value type is VARCHAR(8000) and output string has length longer than 3,999. [504075, System.Data.dll, Bug]
* Fixed error connecting to read only secondary via routing table when connecting using the AOAG listener and specifying Column Encryption Setting=Enabled and ApplicaationIntent=Readonly. [510851, System.Data.dll, Bug]
* Integrating Azure AD Universal and Multi-factor authentication (MFA) support with SQL .NET driver. [521874, System.Data.dll, Feature]
* With this new improvement, the query execution time for enclave based Always Encrypted queries is improved. [524384, System.Data.dll, Feature]
* Signature verification results are now cached improving query execution times for enclave-based queries. [552762, System.Data.dll, Feature]

## WCF
* Fixed service response problems owing to deadlock in SharedTcpTransportManager.OnClose and OnReceiveComplete. [455781, System.ServiceModel.dll, Bug]
* Improved performance in a scenario where an application is using BinaryFormater to serialize/deserialize large number of objects. This fix needs to be opted-into by configuration setting.  [443438, 497686, System.Runtime.Serialization.dll, Bug]
* Improved accessibility for the WCF Service Trace Viewer by updating the focus order of UI components to be more logical [465130, SvcTraceViewer.exe, Bug]
* Improved accessibility for the WCF Service Trace Viewer and the WCF Service Configuration Editor to follow high contrast standards.[505605, SvcConfigEditor.exe, SvcTraceViewer.exe, Bug]
* A race-condition exists in the Abort code-path of SyncDuplexRequest.  When the race-condition occurs, we try to set a ManualResetEvent that has already been closed, which results in an ObjectDisposedException. This happens in one of the threadPool threads and as a result an exception is thrown.  When this happens, the exception crashes the service. [513726, System.Servicemodel.dll, Bug]
* Improved chain trust certificate validation when using certificate authentication with transport security with WCF. With this improvement client certificates that are used to authenticate to a server must be configured for Client Authentication.  Similarly server certificates that are for the authenticating a server must be configured for Server Authentication. With this change if the root certificate is disabled, the certificate chain validation will fail. [516393, System.Servicemodel.dll, Bug]
* Fixed an issue with serializing deeply linked data when using DataContractSerializer. [527549, System.Runtime.Serialization.dll, Bug]

## Windows Forms
* PrivateFontCollection class now releases lock on GDI Fonts that are added to the collection as files [126279, System.Drawing.dll, Bug]
* Fixed a NullReferenceException that would occur when DataGridView.Dispose is called on some systems. [295566, System.Windows.Forms.dll, Bug]
* Fixed problems with DomainUpDown "up" and "down" unsymmetrical operations. [362787, System.Windows.Forms.dll, Bug]
* The arrow of "Type name display style" dropdown button of Document outline window is now painted correctly when it is selected, and HC mode is enabled. This change is effective in applications that were recompiled to target .Net Framework 4.7.2 [386393, System.Windows.Forms.dll, Bug]
* MageUI.exe SDK tool now has localized update units combobox items.  [397545, MageUI.exe, Bug]
* Validation warning dialog in MageUI.exe SDK tool is now localized. [397576, MageUI.exe, Bug]
* Made Culture combobox of Mage UI App/Deployment Manifest Name dialog wider to fit all the text it's items contain [397578, System.Windows.Forms.dll, Bug]
* Narrator now reads out the ToolStripMenuItem accelerator key. [404279, System.Windows.Forms.dll, Bug]
* Improved accessibility for DataGridView control. This change is effective in applications that were recompiled to target .Net Framework 4.7.2 [409783, System.Windows.Forms.dll, Bug]
* Fixed a problem where the child control collection ordering of tab pages could get out of sync with the physical ordering of tabs in a tab control. [411856, System.Windows.Forms.dll, Bug]
* Fixed standard button focus dot line colors in High Contrast mode. [429823, System.Windows.Forms.dll, Bug]
Improved accessibility of the DataGridView control by implementing both Grid and Table UIA patterns. [435320, System.Windows.Forms.dll, Bug]
* Please find the proposed changes here: https://github.com/dotnet/docs/pull/3339 [435621, System.Windows.Forms.dll, Bug]
* Improved keyboard accessibility of ToolStrips hosted in ToolStripContainers. For a Windows Forms application to get all accessibility improvements that were introduced in .NET Framework 4.7.2, the application should be recompiled to target .NET framework 4.7.2 or the application should explicitly opt-in into all accessibility app compat switches in the app.config file. [441148, 518461, System.Windows.Forms.dll, Bug]
* Improved rendering of disabled, FlatStyle=Standard (the default) WinForms RadioButton, CheckBox and GroupBox controls in High Contrast themes. These changes will be effective only on the latest version of Windows 10 (Fall Creator's update), as the corresponding changes in the Windows code are required and in applications that target .Net Framework 4.7.2. [455890, System.Windows.Forms.dll, Bug]
* Made keyboard focus visible in an empty DataGridView control. This change is effective in applications that were recompiled to target .Net Framework 4.7.2 [458754, System.Windows.Forms.dll, Bug]
Improved accessibility for the PropertyGrid, DataGridView, CheckBox, RadioButton and ToolStrip controls. This change is effective in applications that are either recompiled to target .NET Framework 4.7.2, or the following switches are added to the app.config file:
```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" /> 
```
[459106, 497774, 500509, 503194, 508364, 513314, System.Windows.Forms.dll, Bug]
* ContextMenuStrip.SourceControl property now correctly returns the expected control source in nested ToolStripMenuItem cases. [460662, System.Windows.Forms.dll, Bug]
* Fixed a problem introduced in .NET Framework 4.7 in a scenario when a developer uses Configure.Save() method and add an empty section that may not be read while loading project, causing failure in Project load.  [461647, System.Windows.Forms.dll, Bug]
* Updated Open, Save, Undo and Redo icons for WinRes.exe in .NET Framework SDK. [464542, WinRes.exe, Bug]
* MageUI.exe SDK tool now has localized update units combobox items.  [468602, MageUI.exe, Bug]
* Support for PerMovitorV2 DPI awareness in Flat and PopUp ComboBox controls.  [473703, System.Windows.Forms.dll, Bug]
* Fixed text color in pressed and selected modes for toolStripButton, toolStripSplitButton and toolStripDropDownButton in HC Modes. * Fixed arrow color in focused mode for toolStripComboBox in HC Mode.  This change is effective in applications that were recompiled to target .Net Framework 4.7.2 [473866, System.Windows.Forms.dll, Bug]
* MageUI manifest validation prompt header is now fully visible. [475210, MageUI.exe, Bug]
* Improved high contrast experience for DataGridView link cells. This change is effective in applications that were recompiled to target .Net Framework 4.7.2 [475501, System.Windows.Forms.dll, Bug]
* It is possible to switch from designer to property browser of WinRes.exe with F4 key now. It is also possible to switch back using Esc key now. [477857, System.Windows.Forms.dll, Bug]
* Improved discoverability of the ListView control. This change is effective in applications that are either recompiled to target .NET Framework 4.7.2, or the following switches are added to the app.config file:
```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" /> 
```
[484522, System.Windows.Forms.dll, Bug]
* ToolStrip.State will now return AccessibleStates.Unavailable | AccessibleStates.Focused for disabled menu items whereas before it would only return AccessibleStates.Focused. This change enables Narrator to correctly announce the disabled menu items as being disabled. [483700, System.Windows.Forms.dll, Bug]
* Fixed incorrect "..." button text truncation for Mage UI Sign on Save dialog when CHS locale is enabled. [484526, System.Windows.Forms.dll, Bug]
* Resized "Select Culture" dialog of WinRes to make sure that all the text it contains fits the dialog correctly. [488099, WinRes.exe, Bug]
* Implemented Ctrl+Alt+O shortcut to access Output window of WinRes via the keyboard. [513054, System.Windows.Forms.dll, Bug]
* Fixed the narrator focus order for the ClickOnce download progress window. [530637, System.Windows.Forms.dll, Bug]

## Workflow
* In a self-hosted environment when program initialization tasks are executed in parallel and there are common assembly loads happening in each thread, a deadlock could occur. [251926, system.activities.dll, Bug]
* Previously it was possible to encounter a stack overflow in the workflow service hosting process (W3WP.exe) when IWorkflowInstanceManagement.TransactedCancel or IWorkflowInstanceManagement.TransactedTermnate operations were performed. This can be avoided by adding an AppSetting to the Web.Config for the service:
```xml
<appSettings>
<add key="microsoft:WorkflowServices:IgnoreTransactionsForTransactedCancelAndTransactedTerminate" value="true"/>
</appSettings> 
```
The outcome of the transaction does not affect whether the cancel or terminate operation is performed. There is no ""undo"" of a cancel or terminate if the transaction is rolled back. [258978, System.Servicemodel.dll, Bug]
* Improved WorkflowDesignerColors class. [479504, system.activities.dll, Feature]
* Improved accessibility for buttons on workflow designer under HC theme. This change is effective in applications that were recompiled to target .Net Framework 4.7.2 [407093, system.activities.dll, Bug]
* Improved accessibility for workflow activities by removing irrelevant information associated with them. This change is effective in applications that were recompiled to target .NET Framework 4.7.2. [408329, system.activities.dll, Bug]
* Improved accessibility in Workflow designer. Specifically, there are fixes in high contrast mode, focus of different controls and dialogs and name properties. [447654, System.Activities.Presentation.dll, Bug]
* Previously, when using TransactionScopeAsyncFlowOption.Enabled and there you had a non-null Transaction.Current and you did a remote AppDomain call and the lease lifetime expired while that remote AppDomain call was outstanding, Transaction.Current could be null upon return from that call. This is now fixed so that Transaction.Current will be the same after the remote AppDomain call as before the call. [516454, system.transactions.dll, Bug]

## WPF
* Fixed a crash arising when opening a popup within an item in an ItemsControls with VirtualizationMode=Recycling. [161345, PresentationFramework.dll, Bug]
* In Win8+ themes, a disabled Button sets foreground to gray on its ContentPresenter. This inherits to descendants of the ContentPresenter, but not to elements whose logical parent is the Button itself - like the TextBlock. So the Button and its logical child TextBlock kept the default black foreground. This fix removes the setting of foreground on ContentPresenter and sets the foreground on the button to gray, which then extends to its descendants. [204105, PresentationFramework.dll, Bug]
* When an element joins the visual tree, a property can receive an inherited value even when a higher-priority value becomes available at the same time, via a newly-resolvable DynamicResource reference.  This can arise when scrolling a list where VirtualizationMode=Recycling. [208745, PresentationFramework.dll, Bug]
* Fixed a memory leak arising from certain bindings that involve DataSet or related classes (from System.Data.dll). [297912, PresentationFramework.dll, Bug]
* Fixed data corruption arising when a scrolling DataGrid with VirtualizationMode=Recycling. [405066, PresentationFramework.dll, Bug]
* In WPF applications running under certain themes, selected text in TextBox and PasswordBox may not be visible.  This is due to the selection being rendered on top of the text in the Adorner layer.  This feature adds an AppContext switch (Switch.System.Windows.Controls.Text.UseAdornerForTextboxSelectionRendering) that, when set to false, will cause WPF to render the selection underneath the text, allowing for good visibility in TextBox and PasswordBox.  Note that this does not apply to RichTextBox. [405199, PresentationFramework.dll, Bug]
* Applications with multiple hosting layers between WPF and WinForms may experience incorrect focus navigation when pressing the Tab Key. This is now fixed. This change is effective in applications that are either recompiled to target .NET Framework 4.7.2, or the following switches are added to the app.config file:
```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" /> 
```
[445603, PresentationCore.dll, Bug]
* In a master/detail scenario using ADO data, changing the primary key of a master item cleared the display of the corresponding details, with no way to display them thereafter.  This is fixed by default for apps targeting .NET Framework 4.7.2, and for all apps that set the app-context switch ```Switch.System.Windows.Data.DoNotUseFollowParentWhenBindingToADODataRelation``` to false.  [457740, PresentationFramework.dll, Bug]
* Fixed a problem where the keyboard focus visual of Checkbox and RadioButton may be difficult to see in WPF applications running under classic themes or in high contrast scenarios.  This change is effective in applications that are either recompiled to target .NET Framework 4.7.2, or the following switches are added to the app.config file:
```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />  
```
[447590, PresentationFramework.dll, Bug]
* Users may not be able to tab out of a WPF ElementHost contained in a Winforms app when hitting SHIFT + TAB, this issue is fixed now. [458074, WindowsFormsIntegration.dll, Bug]
* Fixed scrolling issues arising in a TreeView that uses VisualStateManager to animate visibility when expanding or collapsing nodes. [460617, PresentationFramework.dll, Bug]
* Improved Keytip behavior to bring parity with behavior on Word and Explorer. Now Keytips would not dismiss a menu launched by mouse. [476533, PresentationFramework.dll, Bug]
* Under certain conditions, a WPF application running on a touch or stylus-enabled machine could possibly see hangs or crashes associated with touch or stylus input.  This would manifest as time spent searching a dictionary on one of the Stylus Input threads.  This change fixes this issue. [485595, PresentationCore.dll, Bug]
* Added a new method to the System.Windows.Diagnostics.ResourceDictionaryDiagnostics class that returns the ResourceDictionaries created for a given source Uri.  This method is for use by diagnostic assistants such as Visual Studio's "UI Debug Tools". [494203, PresentationFramework.dll, Feature]
* Added new methods to the System.Windows.Diagnostics.ResourceDictionaryDiagnostics class that return the owners of a given ResourceDictionary.  These methods are for use by diagnostic assistants such as Visual Studio's "UI Debug Tools". [494205, PresentationFramework.dll, Feature]
* Added a new event to the System.Windows.Diagnostics.ResourceDictionaryDiagnostics class that reports when StaticResource references are resolved.  This event is for use by diagnostic assistants such as Visual Studio's "UI Debug Tools". [494207, PresentationFramework.dll, Feature]
* Fixed rendering issues in Windows Presentation Foundation (WPF) applications that are run within a Windows service that may occur with the September 12, 2017, .NET Security and Quality Rollups that apply to the .NET Framework 4.6, 4.6.1, 4.6.2, and 4.7. [494626, PresentationCore.dll, Bug]
* Reliability improvements for WPF applications running on touch or stylus-enabled machines with long periods of touch inactivity. [514949, PenIMC.dll, Bug]
* In a specific case(s), the System.Windows.Controls.PrintDialog() throws an Arithmetic Overflow exception. This change fixes that issue. [514977, PresentationFramework.dll, Bug]
* A WPF TreeView with virtualization and pixel-scrolling enabled can experience a StackOverflowException due to infinite recursion when (a) all the TreeViewItems have the same height, and (b) the user scrolls to a position just before an item boundary - within a millionth of a pixel. [519728, PresentationFramework.dll, Bug]
* Some dual GPU machines may experience visual artifacts while running WPF apps in high contrast, this issue is now fixed. [525011, PresentationCore.dll, Bug]
* Fixed the issue described in https://github.com/NuGet/Home/issues/5894 [530595, PresentationBuildTasks.dll, Microsoft.WinFX.targets, Bug]
* Applications loading two versions of the same resource assembly may get XamlParseExceptions for resources not found, even when the resource exists in the assembly. This issue is fixed for applications that set the AppContext flag ```Switch.System.Windows.Baml2006.AppendLocalAssemblyVersionForSourceUri``` to false. [546550, PresentationCore.dll; PresentationFramework.dll, Bug]