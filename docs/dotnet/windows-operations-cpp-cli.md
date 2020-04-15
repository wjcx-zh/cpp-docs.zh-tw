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
ms.openlocfilehash: 99fce804ad30e01bdbaa99b1636a5238ff535f8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371777"
---
# <a name="windows-operations-ccli"></a>Windows 作業 (C++/CLI)

使用 Windows SDK 演示各種特定於 Windows 的任務。

以下主題演示了使用可視化C++使用Windows SDK執行的各種Windows操作。

## <a name="determine-if-shutdown-has-started"></a><a name="determine_shutdown"></a>確定關機是否已啟動

以下代碼示例演示如何確定應用程式或 .NET 框架當前是否正在終止。 這對於訪問 .NET Framework 中的靜態元素非常有用,因為在關機期間,這些構造由系統最終確定,無法可靠地使用。 通過首先檢查<xref:System.Environment.HasShutdownStarted%2A>屬性,可以通過不訪問這些元素來避免潛在的故障。

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

## <a name="determine-the-user-interactive-state"></a><a name="determine_user"></a>確定使用者互動狀態

以下代碼示例演示如何確定代碼是否在使用者交互上下文中運行。 如果<xref:System.Environment.UserInteractive%2A>為 false,則代碼作為服務進程或 Web 應用程式內部運行,在這種情況下,不應嘗試與使用者互動。

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

## <a name="read-data-from-the-windows-registry"></a><a name="read_registry"></a>從 Windows 註冊表讀取資料

以下代碼示例使用<xref:Microsoft.Win32.Registry.CurrentUser>密鑰從 Windows 註冊表讀取數據。 首先,使用<xref:Microsoft.Win32.RegistryKey.GetSubKeyNames%2A>方法枚舉子鍵,然後使用方法<xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A>打開標識子鍵。 與根鍵一樣,每個子鍵由<xref:Microsoft.Win32.RegistryKey>類表示。 最後,新<xref:Microsoft.Win32.RegistryKey>物件用於枚舉鍵/值對。

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

類<xref:Microsoft.Win32.Registry>只是的靜態實例的<xref:Microsoft.Win32.RegistryKey>容器。 每個實例表示一個根註冊表節點。 實體<xref:Microsoft.Win32.Registry.ClassesRoot><xref:Microsoft.Win32.Registry.CurrentConfig>是 、、、<xref:Microsoft.Win32.Registry.CurrentUser><xref:Microsoft.Win32.Registry.LocalMachine><xref:Microsoft.Win32.Registry.Users>與 。

除了靜態之外,類中的物件也是唯讀<xref:Microsoft.Win32.Registry>的。 此外,<xref:Microsoft.Win32.RegistryKey>為訪問註冊表物件的內容而創建的類的實例也是唯讀的。 有關如何重寫此行為的示例,請參閱[如何:將數據寫入 Windows 註冊表 (C++/CLI)。](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md)

<xref:Microsoft.Win32.Registry>類別中還有兩個其他物件:<xref:Microsoft.Win32.Registry.DynData><xref:Microsoft.Win32.Registry.PerformanceData>與 。 兩者都是類的<xref:Microsoft.Win32.RegistryKey>實例。 該<xref:Microsoft.Win32.Registry.DynData>物件包含動態註冊表資訊,僅在 Windows 98 和 Windows Me 中支援這些資訊。 該<xref:Microsoft.Win32.Registry.PerformanceData>物件可用於存取使用 Windows 效能監視系統的應用程式的性能計數器資訊。 節點<xref:Microsoft.Win32.Registry.PerformanceData>表示未實際存儲在註冊表中的資訊,因此無法使用 Regedit.exe 查看這些資訊。

## <a name="read-windows-performance-counters"></a><a name="read_performance"></a>讀取 Windows 效能計數器

某些應用程式和 Windows 子系統透過 Windows 效能系統公開效能數據。 可以使用 駐<xref:System.Diagnostics.PerformanceCounterCategory><xref:System.Diagnostics.PerformanceCounter><xref:System.Diagnostics?displayProperty=fullName>留在 命名空間中的和 類訪問這些計數器。

以下代碼示例使用這些類來檢索和顯示由 Windows 更新的計數器,以指示處理器忙的時間百分比。

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

## <a name="retrieve-text-from-the-clipboard"></a><a name="retrieve_text"></a>從剪貼簿檢索文字

以下代碼示例使用<xref:System.Windows.Forms.Clipboard.GetDataObject%2A>成員函數返回指向介面的<xref:System.Windows.Forms.IDataObject>指標。 然後,可以查詢此介面的數據格式,並用於檢索實際數據。

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

## <a name="retrieve-the-current-username"></a><a name="retrieve_current"></a>取索目前使用者名稱

以下代碼示例演示了檢索當前使用者名(登錄到 Windows 的使用者的名稱)。 名稱儲存在字串中<xref:System.Environment.UserName%2A>,該字串在命名空間中<xref:System.Environment>定義。

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

## <a name="retrieve-the-net-framework-version"></a><a name="retrieve_dotnet"></a>取出網路 .NET 架構版本

以下代碼示例演示如何使用<xref:System.Environment.Version%2A>屬性確定當前安裝的 .NET Framework 的版本,該屬性是<xref:System.Version>指向包含版本資訊的物件的指標。

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

## <a name="retrieve-the-local-machine-name"></a><a name="retrieve_local"></a>以索機電腦名稱

以下代碼示例演示了本地電腦名稱(在網路上顯示的計算機名稱)的檢索。 可以通過<xref:System.Environment.MachineName%2A>獲取<xref:System.Environment>在 命名空間中定義的字串來實現此目的。

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

## <a name="retrieve-the-windows-version"></a><a name="retrieve_version"></a>檢索 Windows 版本

以下代碼示例演示如何檢索當前操作系統的平臺和版本資訊。 此資訊儲存在 屬性中<xref:System.Environment.OSVersion%2A?displayProperty=fullName>, 由描述 Windows 廣泛版本的枚舉和包含<xref:System.Environment.Version%2A>作業系統精確構建 的物件組成。

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

## <a name="retrieve-time-elapsed-since-startup"></a><a name="retrieve_time"></a>檢索自啟動以來已過的時間

以下代碼示例演示如何確定刻度計數或自 Windows 啟動以來經過的毫秒數。 此值存儲在成員中<xref:System.Environment.TickCount%2A?displayProperty=fullName>,並且由於它是 32 位值,大約每 24.9 天重置為零。

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

## <a name="store-text-in-the-clipboard"></a><a name="store_text"></a>在剪貼簿中儲存文字

以下代碼示例使用<xref:System.Windows.Forms.Clipboard><xref:System.Windows.Forms>命名空間中定義的物件來儲存字串。 此物件提供兩個成員函數:<xref:System.Windows.Forms.Clipboard.SetDataObject%2A><xref:System.Windows.Forms.Clipboard.GetDataObject%2A>和 。 通過發送派生自<xref:System.Object>的任何物件,<xref:System.Windows.Forms.Clipboard.SetDataObject%2A>資料儲存在剪貼簿中。

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

## <a name="write-data-to-the-windows-registry"></a><a name="write_data"></a>將資料寫入 Windows 註冊表

以下代碼示例使用<xref:Microsoft.Win32.Registry.CurrentUser>鍵創建<xref:Microsoft.Win32.RegistryKey>與**軟體**密鑰對應的類的可寫實例。 然後<xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>,該方法用於創建新鍵並添加到鍵/值對。

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

可以使用 .NET<xref:Microsoft.Win32.Registry>框架<xref:Microsoft.Win32.RegistryKey>使用和 類訪問註冊表,這兩個類都在<xref:Microsoft.Win32>命名空間中 定義。 **註冊表**類是類的靜態實例<xref:Microsoft.Win32.RegistryKey>的 容器。 每個實例表示一個根註冊表節點。 實體<xref:Microsoft.Win32.Registry.ClassesRoot><xref:Microsoft.Win32.Registry.CurrentConfig>是 、、、<xref:Microsoft.Win32.Registry.CurrentUser><xref:Microsoft.Win32.Registry.LocalMachine><xref:Microsoft.Win32.Registry.Users>與 。

## <a name="related-sections"></a>相關章節

<xref:System.Environment>

## <a name="see-also"></a>另請參閱

[.NET 程式設計,帶C++/CLI(視覺C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
