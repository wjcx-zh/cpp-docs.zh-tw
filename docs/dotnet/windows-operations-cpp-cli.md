---
title: Windows 作業 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- Windows [C++], Windows-specific tasks
- .NET Framework [C++], Windows operations
- Visual C++, Windows operations
- Windows operations [C++]
- .NET Framework, shutdown
- shutdown
- termination
- applications [C++], shutdown
- Visual C++, user interactive state
- user interactive state
- Visual C++, reading from Windows Registry
- registry, reading
- performance counters
- performance counters, reading Windows performance counters
- performance monitoring, Windows performance counters
- performance, counters
- counters, reading Windows performance counters
- performance
- performance monitoring
- text, retrieving from Clipboard
- Clipboard, retrieving text
- current user names
- user names, retrieving
- UserName string
- .NET Framework, version
- Version property, retrieving .NET Framework version
- computer name, retrieving
- machine name, retrieving
- computer name
- Windows [C++], version
- Windows [C++], retrieving version using Visual C++
- time, elapsed since startup
- counters, elapsed time
- startup, time elapsed since
- tick counts
- startup
- text, storing in Clipboard
- Clipboard, storing text
- registry, writing to
- Visual C++, writing to Windows Registry
ms.assetid: b9a75cb4-0589-4d5b-92cb-5e8be42b4ac0
ms.openlocfilehash: d23eef1d48674751a725e076d1b652b304ad40a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508390"
---
# <a name="windows-operations-ccli"></a>Windows 作業 (C++/CLI)

示範各種 Windows 特定的工作，使用 Windows SDK。

下列主題會示範各種 Windows 作業執行使用 Visual c + + 的 Windows SDK。

## <a name="determine_shutdown"></a> 判斷是否已開始關機

下列程式碼範例示範如何判斷是否在應用程式或.NET Framework 目前正在終止。 這可用於存取.NET Framework 中的靜態項目，因為在關機時這些建構，系統會完成，且無法可靠地用。 藉由檢查<xref:System.Environment.HasShutdownStarted%2A>屬性第一次，您可以避免潛在的失敗不會存取這些項目。

### <a name="example"></a>範例

```cpp
// check_shutdown.cpp
// compile with: /clr
using namespace System;
int main()
{
   if (Environment::HasShutdownStarted)
      Console::WriteLine("Shutting down.");
   else
      Console::WriteLine("Not shutting down.");
   return 0;
}
```

## <a name="determine_user"></a> 判斷使用者互動狀態

下列程式碼範例示範如何判斷使用者互動的內容中是否正在執行的程式碼。 如果<xref:System.Environment.UserInteractive%2A>為 false，則程式碼執行為服務程序，或從在 Web 應用程式中，在此情況下您不應該嘗試與使用者互動。

### <a name="example"></a>範例

```cpp
// user_interactive.cpp
// compile with: /clr
using namespace System;

int main()
{
   if ( Environment::UserInteractive )
      Console::WriteLine("User interactive");
   else
      Console::WriteLine("Noninteractive");
   return 0;
}
```

## <a name="read_registry"></a> 從 Windows 登錄讀取資料

下列程式碼範例使用<xref:Microsoft.Win32.Registry.CurrentUser>從 Windows 登錄讀取資料的索引鍵。 首先，使用列舉子機碼<xref:Microsoft.Win32.RegistryKey.GetSubKeyNames%2A>方法，然後將身分識別子機碼則使用開啟<xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A>方法。 根目錄機碼，例如每個子機碼由<xref:Microsoft.Win32.RegistryKey>類別。 最後，新<xref:Microsoft.Win32.RegistryKey>物件用來列舉的索引鍵/值組。

### <a name="example"></a>範例

```cpp
// registry_read.cpp
// compile with: /clr
using namespace System;
using namespace Microsoft::Win32;

int main( )
{
   array<String^>^ key = Registry::CurrentUser->GetSubKeyNames( );

   Console::WriteLine("Subkeys within CurrentUser root key:");
   for (int i=0; i<key->Length; i++)
   {
      Console::WriteLine("   {0}", key[i]);
   }

   Console::WriteLine("Opening subkey 'Identities'...");
   RegistryKey^ rk = nullptr;
   rk = Registry::CurrentUser->OpenSubKey("Identities");
   if (rk==nullptr)
   {
      Console::WriteLine("Registry key not found - aborting");
      return -1;
   }

   Console::WriteLine("Key/value pairs within 'Identities' key:");
   array<String^>^ name = rk->GetValueNames( );
   for (int i=0; i<name->Length; i++)
   {
      String^ value = rk->GetValue(name[i])->ToString();
      Console::WriteLine("   {0} = {1}", name[i], value);
   }

   return 0;
}
```

### <a name="remarks"></a>備註

<xref:Microsoft.Win32.Registry>類別是只是靜態的執行個體的容器<xref:Microsoft.Win32.RegistryKey>。 每個執行個體表示的根登錄節點。 執行個體<xref:Microsoft.Win32.Registry.ClassesRoot>， <xref:Microsoft.Win32.Registry.CurrentConfig>， <xref:Microsoft.Win32.Registry.CurrentUser>， <xref:Microsoft.Win32.Registry.LocalMachine>，和<xref:Microsoft.Win32.Registry.Users>。

此外若要在靜態的中的物件<xref:Microsoft.Win32.Registry>類別是唯讀。 此外，執行個體的<xref:Microsoft.Win32.RegistryKey>類別來存取登錄的內容建立的物件也是唯讀。 如需如何覆寫這個行為的範例，請參閱 <<c0> [ 如何： 將資料寫入至 Windows 登錄 (C + + /cli CLI)](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md)。

有兩個額外的物件中<xref:Microsoft.Win32.Registry>類別：<xref:Microsoft.Win32.Registry.DynData>和<xref:Microsoft.Win32.Registry.PerformanceData>。 兩者都是執行個體<xref:Microsoft.Win32.RegistryKey>類別。 <xref:Microsoft.Win32.Registry.DynData>物件包含動態登錄資訊，只支援 Windows 98 和 Windows me。 <xref:Microsoft.Win32.Registry.PerformanceData>物件可以用來存取使用 Windows 效能監視系統的應用程式的效能計數器資訊。 <xref:Microsoft.Win32.Registry.PerformanceData>節點表示資訊不會實際儲存在登錄中，因此無法檢視使用 Regedit.exe。

## <a name="read_performance"></a> 讀取 Windows 效能計數器

某些應用程式和 Windows 子系統會公開透過 Windows 效能系統的效能資料。 這些計數器可以使用來存取<xref:System.Diagnostics.PerformanceCounterCategory>並<xref:System.Diagnostics.PerformanceCounter>類別，位於<xref:System.Diagnostics?displayProperty=fullName>命名空間。

下列程式碼範例會使用這些類別來擷取並顯示更新的 Windows，以指出在處理器處於忙碌的時間的百分比計數器。

> [!NOTE]
>  這個範例需要系統管理權限才能在 Windows Vista 上執行。

### <a name="example"></a>範例

```cpp
// processor_timer.cpp
// compile with: /clr
#using <system.dll>

using namespace System;
using namespace System::Threading;
using namespace System::Diagnostics;
using namespace System::Timers;

ref struct TimerObject
{
public:
   static String^ m_instanceName;
   static PerformanceCounter^ m_theCounter;

public:
   static void OnTimer(Object^ source, ElapsedEventArgs^ e)
   {
      try
      {
         Console::WriteLine("CPU time used: {0,6} ",
          m_theCounter->NextValue( ).ToString("f"));
      }
      catch(Exception^ e)
      {
         if (dynamic_cast<InvalidOperationException^>(e))
         {
            Console::WriteLine("Instance '{0}' does not exist",
                  m_instanceName);
            return;
         }
         else
         {
            Console::WriteLine("Unknown exception... ('q' to quit)");
            return;
         }
      }
   }
};

int main()
{
   String^ objectName = "Processor";
   String^ counterName = "% Processor Time";
   String^ instanceName = "_Total";

   try
   {
      if ( !PerformanceCounterCategory::Exists(objectName) )
      {
         Console::WriteLine("Object {0} does not exist", objectName);
         return -1;
      }
   }
   catch (UnauthorizedAccessException ^ex)
   {
      Console::WriteLine("You are not authorized to access this information.");
      Console::Write("If you are using Windows Vista, run the application with ");
      Console::WriteLine("administrative privileges.");
      Console::WriteLine(ex->Message);
      return -1;
   }

   if ( !PerformanceCounterCategory::CounterExists(
          counterName, objectName) )
   {
      Console::WriteLine("Counter {0} does not exist", counterName);
      return -1;
   }

   TimerObject::m_instanceName = instanceName;
   TimerObject::m_theCounter = gcnew PerformanceCounter(
          objectName, counterName, instanceName);

   System::Timers::Timer^ aTimer = gcnew System::Timers::Timer();
   aTimer->Elapsed += gcnew ElapsedEventHandler(&TimerObject::OnTimer);
   aTimer->Interval = 1000;
   aTimer->Enabled = true;
   aTimer->AutoReset = true;

   Console::WriteLine("reporting CPU usage for the next 10 seconds");
   Thread::Sleep(10000);
   return 0;
}
```

## <a name="retrieve_text"></a> 從剪貼簿擷取文字

下列程式碼範例會使用<xref:System.Windows.Forms.Clipboard.GetDataObject%2A>成員函式傳回的指標<xref:System.Windows.Forms.IDataObject>介面。 可以查詢的資料格式的這個介面，然後用來擷取實際的資料。

### <a name="example"></a>範例

```cpp
// read_clipboard.cpp
// compile with: /clr
#using <system.dll>
#using <system.Drawing.dll>
#using <system.windows.forms.dll>

using namespace System;
using namespace System::Windows::Forms;

[STAThread] int main( )
{
   IDataObject^ data = Clipboard::GetDataObject( );

   if (data)
   {
      if (data->GetDataPresent(DataFormats::Text))
      {
         String^ text = static_cast<String^>
           (data->GetData(DataFormats::Text));
         Console::WriteLine(text);
      }
      else
         Console::WriteLine("Nontext data is in the Clipboard.");
   }
   else
   {
      Console::WriteLine("No data was found in the Clipboard.");
   }

   return 0;
}
```

## <a name="retrieve_current"></a> 擷取目前的使用者名稱

下列程式碼範例示範如何擷取目前的使用者名稱 （登入 Windows 的使用者名稱）。 名稱會儲存在<xref:System.Environment.UserName%2A>字串，其定義於<xref:System.Environment>命名空間。

### <a name="example"></a>範例

```cpp
// username.cpp
// compile with: /clr
using namespace System;

int main()
{
   Console::WriteLine("\nCurrent user: {0}", Environment::UserName);
   return 0;
}
```

## <a name="retrieve_dotnet"></a> 擷取.NET Framework 版本

下列程式碼範例示範如何判斷目前已安裝.NET Framework 版本<xref:System.Environment.Version%2A>屬性，這是一個指標至<xref:System.Version>物件，包含版本資訊。

### <a name="example"></a>範例

```cpp
// dotnet_ver.cpp
// compile with: /clr
using namespace System;
int main()
{
   Version^ version = Environment::Version;
   if (version)
   {
      int build = version->Build;
      int major = version->Major;
      int minor = version->Minor;
      int revision = Environment::Version->Revision;
      Console::Write(".NET Framework version: ");
      Console::WriteLine("{0}.{1}.{2}.{3}",
            build, major, minor, revision);
   }
   return 0;
}
```

## <a name="retrieve_local"></a> 擷取本機電腦名稱

下列程式碼範例示範如何擷取本機電腦名稱 （因為它的電腦名稱會出現在網路上）。 您可以取得來完成這<xref:System.Environment.MachineName%2A>字串，其定義於<xref:System.Environment>命名空間。

### <a name="example"></a>範例

```cpp
// machine_name.cpp
// compile with: /clr
using namespace System;

int main()
{
   Console::WriteLine("\nMachineName: {0}", Environment::MachineName);
   return 0;
}
```

## <a name="retrieve_version"></a> 擷取 Windows 版本

下列程式碼範例示範如何擷取目前的作業系統的平台和版本資訊。 這項資訊會儲存在<xref:System.Environment.OSVersion%2A?displayProperty=fullName>屬性和列舉型別描述廣義的 Windows 版本所組成，<xref:System.Environment.Version%2A>物件，其中包含作業系統的確切組建。

### <a name="example"></a>範例

```cpp
// os_ver.cpp
// compile with: /clr
using namespace System;

int main()
{
   OperatingSystem^ osv = Environment::OSVersion;
   PlatformID id = osv->Platform;
   Console::Write("Operating system: ");

   if (id == PlatformID::Win32NT)
      Console::WriteLine("Win32NT");
   else if (id == PlatformID::Win32S)
      Console::WriteLine("Win32S");
   else if (id == PlatformID::Win32Windows)
      Console::WriteLine("Win32Windows");
   else
      Console::WriteLine("WinCE");

   Version^ version = osv->Version;
   if (version)
   {
      int build = version->Build;
      int major = version->Major;
      int minor = version->Minor;
      int revision = Environment::Version->Revision;
      Console::Write("OS Version: ");
      Console::WriteLine("{0}.{1}.{2}.{3}",
                   build, major, minor, revision);
   }

   return 0;
}
```

## <a name="retrieve_time"></a> 自啟動後經過的擷取時間

下列程式碼範例示範如何判斷滴答計數，或啟動的 Windows 以來所經過的毫秒數。 這個值會儲存在<xref:System.Environment.TickCount%2A?displayProperty=fullName>成員，因為它是 32 位元值時，會重設為零大約每隔 24.9 天。

### <a name="example"></a>範例

```cpp
// startup_time.cpp
// compile with: /clr
using namespace System;

int main( )
{
   Int32 tc = Environment::TickCount;
   Int32 seconds = tc / 1000;
   Int32 minutes = seconds / 60;
   float hours = static_cast<float>(minutes) / 60;
   float days = hours / 24;

   Console::WriteLine("Milliseconds since startup: {0}", tc);
   Console::WriteLine("Seconds since startup: {0}", seconds);
   Console::WriteLine("Minutes since startup: {0}", minutes);
   Console::WriteLine("Hours since startup: {0}", hours);
   Console::WriteLine("Days since startup: {0}", days);

   return 0;
}
```

## <a name="store_text"></a> 將文字儲存在剪貼簿

下列程式碼範例會使用<xref:System.Windows.Forms.Clipboard>中所定義的物件<xref:System.Windows.Forms>命名空間來儲存字串。 這個物件提供兩個成員函式：<xref:System.Windows.Forms.Clipboard.SetDataObject%2A>和<xref:System.Windows.Forms.Clipboard.GetDataObject%2A>。 資料時，會儲存在剪貼簿上，藉由傳送任何物件衍生自<xref:System.Object>至<xref:System.Windows.Forms.Clipboard.SetDataObject%2A>。

### <a name="example"></a>範例

```cpp
// store_clipboard.cpp
// compile with: /clr
#using <System.dll>
#using <System.Drawing.dll>
#using <System.Windows.Forms.dll>

using namespace System;
using namespace System::Windows::Forms;

[STAThread] int main()
{
   String^ str = "This text is copied into the Clipboard.";

   // Use 'true' as the second argument if
   // the data is to remain in the clipboard
   // after the program terminates.
   Clipboard::SetDataObject(str, true);

   Console::WriteLine("Added text to the Clipboard.");

   return 0;
}
```

## <a name="write_data"></a> 將資料寫入至 Windows 登錄

下列程式碼範例會使用<xref:Microsoft.Win32.Registry.CurrentUser>要建立的可寫入執行個體索引鍵<xref:Microsoft.Win32.RegistryKey>類別對應至**軟體**索引鍵。 <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>方法則用來建立新的金鑰，並將新增至索引鍵/值組。

### <a name="example"></a>範例

```cpp
// registry_write.cpp
// compile with: /clr
using namespace System;
using namespace Microsoft::Win32;

int main()
{
   // The second OpenSubKey argument indicates that
   // the subkey should be writable.
   RegistryKey^ rk;
   rk  = Registry::CurrentUser->OpenSubKey("Software", true);
   if (!rk)
   {
      Console::WriteLine("Failed to open CurrentUser/Software key");
      return -1;
   }

   RegistryKey^ nk = rk->CreateSubKey("NewRegKey");
   if (!nk)
   {
      Console::WriteLine("Failed to create 'NewRegKey'");
      return -1;
   }

   String^ newValue = "NewValue";
   try
   {
      nk->SetValue("NewKey", newValue);
      nk->SetValue("NewKey2", 44);
   }
   catch (Exception^)
   {
      Console::WriteLine("Failed to set new values in 'NewRegKey'");
      return -1;
   }

   Console::WriteLine("New key created.");
   Console::Write("Use REGEDIT.EXE to verify ");
   Console::WriteLine("'CURRENTUSER/Software/NewRegKey'\n");
   return 0;
}
```

### <a name="remarks"></a>備註

您可用來存取登錄中的以.NET Framework<xref:Microsoft.Win32.Registry>並[RegistryKey](https://msdn.microsoft.com/library/microsoft.win32.registrykey.aspx)類別，這兩者都定義在<xref:Microsoft.Win32>命名空間。 **登錄**類別是靜態的執行個體的容器<xref:Microsoft.Win32.RegistryKey>類別。 每個執行個體表示的根登錄節點。 執行個體<xref:Microsoft.Win32.Registry.ClassesRoot>， <xref:Microsoft.Win32.Registry.CurrentConfig>， <xref:Microsoft.Win32.Registry.CurrentUser>， <xref:Microsoft.Win32.Registry.LocalMachine>，和<xref:Microsoft.Win32.Registry.Users>。

## <a name="related-sections"></a>相關章節

<xref:System.Environment>

## <a name="see-also"></a>另請參閱

[以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
