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
ms.openlocfilehash: 3c4ef2a69c25313ff444e0fabaea6eef2feeeee2
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501655"
---
# <a name="windows-operations-ccli"></a>Windows 作業 (C++/CLI)

使用 Windows SDK 示範各種 Windows 特定的工作。

下列主題示範使用 Visual C++ 搭配 Windows SDK 執行的各種 Windows 作業。

## <a name="determine-if-shutdown-has-started"></a><a name="determine_shutdown"></a> 判斷關機是否已啟動

下列程式碼範例示範如何判斷應用程式或 .NET Framework 目前是否正在終止。 這有助於存取 .NET Framework 中的靜態元素，因為在關機期間，這些結構會由系統完成，而且無法可靠地使用。 藉由 <xref:System.Environment.HasShutdownStarted%2A> 先檢查屬性，您就可以不存取這些元素來避免可能的失敗。

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

## <a name="determine-the-user-interactive-state"></a><a name="determine_user"></a> 判斷使用者互動狀態

下列程式碼範例示範如何判斷程式碼是否正在使用者互動的內容中執行。 如果 <xref:System.Environment.UserInteractive%2A> 為 false，則程式碼會以服務進程的形式執行，或從 Web 應用程式內部執行，在這種情況下，您不應該嘗試與使用者互動。

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

## <a name="read-data-from-the-windows-registry"></a><a name="read_registry"></a> 從 Windows 登錄讀取資料

下列程式碼範例會使用 <xref:Microsoft.Win32.Registry.CurrentUser> 金鑰來讀取 Windows 登錄中的資料。 首先，系統會使用方法來列舉子機碼 <xref:Microsoft.Win32.RegistryKey.GetSubKeyNames%2A> ，然後使用方法開啟身分識別子機碼 <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> 。 和根金鑰一樣，每個子機碼都是由 <xref:Microsoft.Win32.RegistryKey> 類別表示。 最後，新的 <xref:Microsoft.Win32.RegistryKey> 物件會用來列舉索引鍵/值組。

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

<xref:Microsoft.Win32.Registry>類別只是靜態實例的容器 <xref:Microsoft.Win32.RegistryKey> 。 每個實例都代表一個根登錄節點。 實例為 <xref:Microsoft.Win32.Registry.ClassesRoot> 、、 <xref:Microsoft.Win32.Registry.CurrentConfig> <xref:Microsoft.Win32.Registry.CurrentUser> 、 <xref:Microsoft.Win32.Registry.LocalMachine> 和 <xref:Microsoft.Win32.Registry.Users> 。

除了為靜態，類別內的物件 <xref:Microsoft.Win32.Registry> 也是唯讀的。 此外， <xref:Microsoft.Win32.RegistryKey> 為了存取登錄物件的內容而建立的類別實例也是唯讀的。 如需如何覆寫此行為的範例，請參閱 [如何：將資料寫入 Windows 登錄 (c + +/cli) ](#write_data)。

類別中有兩個額外的物件 <xref:Microsoft.Win32.Registry> ： <xref:Microsoft.Win32.Registry.DynData> 和 <xref:Microsoft.Win32.Registry.PerformanceData> 。 兩者都是類別的實例 <xref:Microsoft.Win32.RegistryKey> 。 此 <xref:Microsoft.Win32.Registry.DynData> 物件包含動態登錄資訊，只有在 Windows 98 和 Windows Me 中才支援。 <xref:Microsoft.Win32.Registry.PerformanceData>物件可以用來存取使用 Windows 效能監視系統之應用程式的效能計數器資訊。 <xref:Microsoft.Win32.Registry.PerformanceData>節點代表未實際儲存在登錄中，因此無法使用 Regedit.exe 來查看的資訊。

## <a name="read-windows-performance-counters"></a><a name="read_performance"></a> 讀取 Windows 效能計數器

某些應用程式和 Windows 子系統會透過 Windows 效能系統公開效能資料。 您可以使用 <xref:System.Diagnostics.PerformanceCounterCategory> <xref:System.Diagnostics.PerformanceCounter> 位於命名空間中的和類別來存取這些計數器 <xref:System.Diagnostics?displayProperty=fullName> 。

下列程式碼範例會使用這些類別來取出並顯示由 Windows 更新的計數器，以指出處理器忙碌的時間百分比。

> [!NOTE]
> 這個範例需要系統管理權限才能在 Windows Vista 上執行。

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

## <a name="retrieve-text-from-the-clipboard"></a><a name="retrieve_text"></a> 從剪貼簿取出文字

下列程式碼範例會使用 <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> 成員函式，將指標傳回至 <xref:System.Windows.Forms.IDataObject> 介面。 然後可以查詢此介面，以取得資料的格式，並用來取得實際的資料。

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

## <a name="retrieve-the-current-username"></a><a name="retrieve_current"></a> 取出目前的使用者名稱

下列程式碼範例將示範如何抓取目前的使用者名稱， (登入 Windows) 的使用者名稱。 名稱會儲存在 <xref:System.Environment.UserName%2A> 命名空間中定義的字串中 <xref:System.Environment> 。

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

## <a name="retrieve-the-net-framework-version"></a><a name="retrieve_dotnet"></a> 取出 .NET Framework 版本

下列程式碼範例示範如何使用屬性來判斷目前安裝 .NET Framework 的版本 <xref:System.Environment.Version%2A> ，這是 <xref:System.Version> 包含版本資訊之物件的指標。

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

## <a name="retrieve-the-local-machine-name"></a><a name="retrieve_local"></a> 取出本機電腦名稱稱

下列程式碼範例將示範如何抓取本機電腦名稱稱， (在網路) 上顯示的電腦名稱稱。 您可以藉由取得在 <xref:System.Environment.MachineName%2A> 命名空間中定義的字串來完成此動作 <xref:System.Environment> 。

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

## <a name="retrieve-the-windows-version"></a><a name="retrieve_version"></a> 取出 Windows 版本

下列程式碼範例示範如何取出目前作業系統的平臺和版本資訊。 這項資訊會儲存在 <xref:System.Environment.OSVersion%2A?displayProperty=fullName> 屬性中，並包含一個列舉，描述廣泛詞彙的 Windows 版本，以及 <xref:System.Environment.Version%2A> 包含作業系統確切組建的物件。

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

## <a name="retrieve-time-elapsed-since-startup"></a><a name="retrieve_time"></a> 從啟動以來取出經過的時間

下列程式碼範例示範如何判斷滴答計數，或自啟動 Windows 以來經過的毫秒數。 此值會儲存在 <xref:System.Environment.TickCount%2A?displayProperty=fullName> 成員中，而且因為它是32位的值，所以大約每隔24.9 天重設為零。

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

## <a name="store-text-in-the-clipboard"></a><a name="store_text"></a> 儲存剪貼簿中的文字

下列程式碼範例使用 <xref:System.Windows.Forms.Clipboard> 命名空間中定義的物件 <xref:System.Windows.Forms> 來儲存字串。 這個物件會提供兩個成員函式： <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> 和 <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> 。 資料會藉由傳送任何衍生自的物件，儲存在剪貼簿中 <xref:System.Object> <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> 。

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

## <a name="write-data-to-the-windows-registry"></a><a name="write_data"></a> 將資料寫入 Windows 登錄

下列程式碼範例會使用 <xref:Microsoft.Win32.Registry.CurrentUser> 金鑰來建立 <xref:Microsoft.Win32.RegistryKey> 對應至 **軟體** 金鑰之類別的可寫入實例。 <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>接著會使用方法來建立新的索引鍵，並將其新增至索引鍵/值組。

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

您可以使用 .NET Framework 來存取具有 <xref:Microsoft.Win32.Registry> 和 <xref:Microsoft.Win32.RegistryKey> 類別的登錄，這些類別都是在 <xref:Microsoft.Win32> 命名空間中定義。 登錄 **類別是** 類別靜態實例的容器 <xref:Microsoft.Win32.RegistryKey> 。 每個實例都代表一個根登錄節點。 實例為 <xref:Microsoft.Win32.Registry.ClassesRoot> 、、 <xref:Microsoft.Win32.Registry.CurrentConfig> <xref:Microsoft.Win32.Registry.CurrentUser> 、 <xref:Microsoft.Win32.Registry.LocalMachine> 和 <xref:Microsoft.Win32.Registry.Users> 。

## <a name="related-sections"></a>相關章節

<xref:System.Environment>

## <a name="see-also"></a>另請參閱

[使用 c + +/CLI 進行 .NET 程式設計 (Visual C++) ](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
