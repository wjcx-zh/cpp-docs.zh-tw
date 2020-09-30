---
title: '檔案處理和 i/o (c + +/CLI) '
ms.date: 11/04/2016
helpviewer_keywords:
- .NET Framework [C++], file handling
- files [C++], .NET Framework and
- I/O [C++], .NET Framework applications
- .NET Framework [C++], I/O
- files [C++], listing files
- directories [C++], listing files
- monitoring file system events
- FileSystemWatcher class, examples
- examples [C++], monitoring file system changes
- events [C++], monitoring
- file system events [C++]
- files [C++], binary
- binary files, reading in C++
- reading text files
- text files, reading
- files [C++], retrieving information about
- FileInfo class
- binary files, writing in C++
- files [C++], binary
- files [C++], text
- text files, writing in C++
ms.assetid: 3296fd59-a83a-40d4-bd4a-6096cc13101b
ms.openlocfilehash: a1cfdc4239506f22368753d8c37765e550d9b835
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508940"
---
# <a name="file-handling-and-io-ccli"></a>檔案處理和 I/O (C++/CLI)

示範使用 .NET Framework 的各種檔案作業。

下列主題示範如何使用命名空間中定義的類別 <xref:System.IO> 來執行各種檔案作業。

## <a name="enumerate-files-in-a-directory"></a><a name="enumerate"></a> 列舉目錄中的檔案

下列程式碼範例示範如何取出目錄中的檔案清單。 此外，也會列舉子目錄。 下列程式碼範例會使用 <xref:System.IO.Directory.GetFiles%2A> <xref:System.IO.Directory.GetFiles%2A> 和 <xref:System.IO.Directory.GetDirectories%2A> 方法來顯示 C：\Windows 目錄的內容。

### <a name="example"></a>範例

```cpp
// enum_files.cpp
// compile with: /clr
using namespace System;
using namespace System::IO;

int main()
{
   String^ folder = "C:\\";
   array<String^>^ dir = Directory::GetDirectories( folder );
   Console::WriteLine("--== Directories inside '{0}' ==--", folder);
   for (int i=0; i<dir->Length; i++)
      Console::WriteLine(dir[i]);

   array<String^>^ file = Directory::GetFiles( folder );
   Console::WriteLine("--== Files inside '{0}' ==--", folder);
   for (int i=0; i<file->Length; i++)
      Console::WriteLine(file[i]);

   return 0;
}
```

## <a name="monitor-file-system-changes"></a><a name="monitor"></a> 監視檔案系統變更

下列程式碼範例會使用 <xref:System.IO.FileSystemWatcher> 來註冊對應至所建立、變更、刪除或重新命名之檔案的事件。 您可以使用 <xref:System.IO.FileSystemWatcher> 類別，在偵測到變更時引發事件，而不是定期輪詢目錄以變更檔案。

### <a name="example"></a>範例

```cpp
// monitor_fs.cpp
// compile with: /clr
#using <system.dll>

using namespace System;
using namespace System::IO;

ref class FSEventHandler
{
public:
    void OnChanged (Object^ source, FileSystemEventArgs^ e)
    {
        Console::WriteLine("File: {0} {1}",
               e->FullPath, e->ChangeType);
    }
    void OnRenamed(Object^ source, RenamedEventArgs^ e)
    {
        Console::WriteLine("File: {0} renamed to {1}",
                e->OldFullPath, e->FullPath);
    }
};

int main()
{
   array<String^>^ args = Environment::GetCommandLineArgs();

   if(args->Length < 2)
   {
      Console::WriteLine("Usage: Watcher.exe <directory>");
      return -1;
   }

   FileSystemWatcher^ fsWatcher = gcnew FileSystemWatcher( );
   fsWatcher->Path = args[1];
   fsWatcher->NotifyFilter = static_cast<NotifyFilters>
              (NotifyFilters::FileName |
               NotifyFilters::Attributes |
               NotifyFilters::LastAccess |
               NotifyFilters::LastWrite |
               NotifyFilters::Security |
               NotifyFilters::Size );

    FSEventHandler^ handler = gcnew FSEventHandler();
    fsWatcher->Changed += gcnew FileSystemEventHandler(
            handler, &FSEventHandler::OnChanged);
    fsWatcher->Created += gcnew FileSystemEventHandler(
            handler, &FSEventHandler::OnChanged);
    fsWatcher->Deleted += gcnew FileSystemEventHandler(
            handler, &FSEventHandler::OnChanged);
    fsWatcher->Renamed += gcnew RenamedEventHandler(
            handler, &FSEventHandler::OnRenamed);

    fsWatcher->EnableRaisingEvents = true;

    Console::WriteLine("Press Enter to quit the sample.");
    Console::ReadLine( );
}
```

## <a name="read-a-binary-file"></a><a name="read_binary"></a> 讀取二進位檔案

下列程式碼範例顯示如何使用命名空間中的兩個類別，從檔案讀取二進位資料 <xref:System.IO?displayProperty=fullName> ： <xref:System.IO.FileStream> 和 <xref:System.IO.BinaryReader> 。 <xref:System.IO.FileStream> 表示實際的檔案。 <xref:System.IO.BinaryReader> 提供允許二進位存取之資料流程的介面。

程式碼範例會讀取名為 data 的檔案，並包含二進位格式的整數。 如需這種檔案的相關資訊，請參閱 [如何： (c + +/Cli 寫入二進位檔案) ](#write_binary)。

### <a name="example"></a>範例

```cpp
// binary_read.cpp
// compile with: /clr
#using<system.dll>
using namespace System;
using namespace System::IO;

int main()
{
   String^ fileName = "data.bin";
   try
   {
      FileStream^ fs = gcnew FileStream(fileName, FileMode::Open);
      BinaryReader^ br = gcnew BinaryReader(fs);

      Console::WriteLine("contents of {0}:", fileName);
      while (br->BaseStream->Position < br->BaseStream->Length)
         Console::WriteLine(br->ReadInt32().ToString());

      fs->Close( );
   }
   catch (Exception^ e)
   {
      if (dynamic_cast<FileNotFoundException^>(e))
         Console::WriteLine("File '{0}' not found", fileName);
      else
         Console::WriteLine("Exception: ({0})", e);
      return -1;
   }
   return 0;
}
```

## <a name="read-a-text-file"></a><a name="read_text"></a> 讀取文字檔

下列程式碼範例示範如何使用 <xref:System.IO.StreamReader> 命名空間中定義的類別，一次開啟和讀取文字檔 <xref:System.IO?displayProperty=fullName> 。 這個類別的實例是用來開啟文字檔，然後 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=fullName> 使用方法來取出每一行。

這個程式碼範例會讀取名為 textfile.txt 的檔案，並包含文字。 如需這種檔案的相關資訊，請參閱 [如何： (c + +/Cli 撰寫文字檔) ](#write_text)。

### <a name="example"></a>範例

```cpp
// text_read.cpp
// compile with: /clr
#using<system.dll>
using namespace System;
using namespace System::IO;

int main()
{
   String^ fileName = "textfile.txt";
   try
   {
      Console::WriteLine("trying to open file {0}...", fileName);
      StreamReader^ din = File::OpenText(fileName);

      String^ str;
      int count = 0;
      while ((str = din->ReadLine()) != nullptr)
      {
         count++;
         Console::WriteLine("line {0}: {1}", count, str );
      }
   }
   catch (Exception^ e)
   {
      if (dynamic_cast<FileNotFoundException^>(e))
         Console::WriteLine("file '{0}' not found", fileName);
      else
         Console::WriteLine("problem reading file '{0}'", fileName);
   }

   return 0;
}
```

## <a name="retrieve-file-information"></a><a name="retrieve"></a> 取出檔案資訊

下列程式碼範例將示範 <xref:System.IO.FileInfo> 類別。 當您擁有檔案的名稱時，您可以使用這個類別來取得檔案的相關資訊，例如檔案大小、目錄、完整名稱，以及建立的日期和時間，以及上次修改的日期和時間。

此程式碼會抓取 Notepad.exe 的檔案資訊。

### <a name="example"></a>範例

```cpp
// file_info.cpp
// compile with: /clr
using namespace System;
using namespace System::IO;

int main()
{
   array<String^>^ args = Environment::GetCommandLineArgs();
   if (args->Length < 2)
   {
      Console::WriteLine("\nUSAGE : file_info <filename>\n\n");
      return -1;
   }

   FileInfo^ fi = gcnew FileInfo( args[1] );

   Console::WriteLine("file size: {0}", fi->Length );

   Console::Write("File creation date:  ");
   Console::Write(fi->CreationTime.Month.ToString());
   Console::Write(".{0}", fi->CreationTime.Day.ToString());
   Console::WriteLine(".{0}", fi->CreationTime.Year.ToString());

   Console::Write("Last access date:  ");
   Console::Write(fi->LastAccessTime.Month.ToString());
   Console::Write(".{0}", fi->LastAccessTime.Day.ToString());
   Console::WriteLine(".{0}", fi->LastAccessTime.Year.ToString());

   return 0;
}
```

## <a name="write-a-binary-file"></a><a name="write_binary"></a> 寫入二進位檔案

下列程式碼範例示範如何將二進位資料寫入檔案。 使用命名空間的兩個類別 <xref:System.IO> ： <xref:System.IO.FileStream> 和 <xref:System.IO.BinaryWriter> 。 <xref:System.IO.FileStream> 表示實際的檔案，並 <xref:System.IO.BinaryWriter> 提供允許二進位存取之資料流程的介面。

下列程式碼範例會寫入檔案，其中包含二進位格式的整數。 您可以使用 [如何：讀取二進位檔案 (c + +/cli) ](#read_binary)中的程式碼來讀取此檔案。

### <a name="example"></a>範例

```cpp
// binary_write.cpp
// compile with: /clr
#using<system.dll>
using namespace System;
using namespace System::IO;

int main()
{
   array<Int32>^ data = {1, 2, 3, 10000};

   FileStream^ fs = gcnew FileStream("data.bin", FileMode::Create);
   BinaryWriter^ w = gcnew BinaryWriter(fs);

   try
   {
      Console::WriteLine("writing data to file:");
      for (int i=0; i<data->Length; i++)
      {
         Console::WriteLine(data[i]);
         w->Write(data[i]);
      }
   }
   catch (Exception^)
   {
     Console::WriteLine("data could not be written");
     fs->Close();
     return -1;
   }

   fs->Close();
   return 0;
}
```

## <a name="write-a-text-file"></a><a name="write_text"></a> 寫入文字檔

下列程式碼範例示範如何建立文字檔，並使用在 <xref:System.IO.StreamWriter> 命名空間中定義的類別，將文字寫入其中 <xref:System.IO> 。 此函式 <xref:System.IO.StreamWriter> 會使用要建立的檔案名。 如果檔案存在，則會覆寫 (除非您傳遞 True 做為第二個函式 <xref:System.IO.StringWriter> 引數) 。

然後，會使用和函式來將檔案歸檔 <xref:System.IO.StreamWriter.Write%2A> <xref:System.IO.TextWriter.WriteLine%2A> 。

### <a name="example"></a>範例

```cpp
// text_write.cpp
// compile with: /clr
using namespace System;
using namespace System::IO;

int main()
{
   String^ fileName = "textfile.txt";

   StreamWriter^ sw = gcnew StreamWriter(fileName);
   sw->WriteLine("A text file is born!");
   sw->Write("You can use WriteLine");
   sw->WriteLine("...or just Write");
   sw->WriteLine("and do {0} output too.", "formatted");
   sw->WriteLine("You can also send non-text objects:");
   sw->WriteLine(DateTime::Now);
   sw->Close();
   Console::WriteLine("a new file ('{0}') has been written", fileName);

   return 0;
}
```

## <a name="see-also"></a>另請參閱

[使用 c + +/CLI 進行 .NET 程式設計 (Visual C++) ](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[檔案和資料流程 i/o](/dotnet/standard/io/index)<br/>
[System.IO 命名空間](/dotnet/api/system.io)
