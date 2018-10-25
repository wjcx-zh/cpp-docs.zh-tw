---
title: 檔案處理和 I-o (C + + /cli CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f6fa8dcf1488b693b53cde591c548122767f1af7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50075108"
---
# <a name="file-handling-and-io-ccli"></a>檔案處理和 I/O (C++/CLI)
示範如何使用.NET Framework 的各種檔案作業。

下列主題示範如何使用類別中定義<xref:System.IO>命名空間，以執行各種檔案作業。

## <a name="enumerate"></a> 列舉目錄中的檔案

下列程式碼範例示範如何擷取目錄中檔案的清單。 此外，也會列舉子目錄。 下列程式碼範例會使用<xref:System.IO.Directory.GetFiles%2A><xref:System.IO.Directory.GetFiles%2A>和<xref:System.IO.Directory.GetDirectories%2A>方法以顯示 C:\Windows 目錄的內容。

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

## <a name="monitor"></a> 監視檔案系統變更

下列程式碼範例使用<xref:System.IO.FileSystemWatcher>註冊建立、 變更、 刪除或重新命名的檔案對應的事件。 除了定期輪詢變更檔案的目錄，您可以使用<xref:System.IO.FileSystemWatcher>類別來引發事件時偵測到變更。

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

## <a name="read_binary"></a> 讀取二進位檔案

下列程式碼範例示範如何從檔案讀取二進位資料，藉由使用中的兩個類別<xref:System.IO?displayProperty=fullName>命名空間：<xref:System.IO.FileStream>和<xref:System.IO.BinaryReader>。 <xref:System.IO.FileStream> 代表實際的檔案。 <xref:System.IO.BinaryReader> 提供可進行二進位存取的資料流介面。

在程式碼範例會讀取名為 data.bin 且包含二進位格式整數的檔案。 如需這類檔案的詳細資訊，請參閱 <<c0> [ 如何： 寫入二進位檔案 (C + + /cli CLI)](../dotnet/how-to-write-a-binary-file-cpp-cli.md)。

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

## <a name="read_text"></a> 讀取文字檔

下列程式碼範例示範如何開啟並讀取一次的文字檔案的一行，使用<xref:System.IO.StreamReader>中所定義的類別<xref:System.IO?displayProperty=fullName>命名空間。 此類別的執行個體用來開啟文字檔案，然後<xref:System.IO.StreamReader.ReadLine%2A?displayProperty=fullName>方法用來擷取每一行。

此程式碼範例會讀取名為 textfile.txt 且包含文字的檔案。 如需這類檔案的詳細資訊，請參閱 <<c0> [ 如何： 寫入文字檔 (C + + /cli CLI)](../dotnet/how-to-write-a-text-file-cpp-cli.md)。

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

## <a name="retrieve"></a> 擷取檔案資訊

下列程式碼範例示範<xref:System.IO.FileInfo>類別。 當您有檔案的名稱時，您可以使用這個類別來擷取相關的檔案，例如檔案大小、 目錄、 完整名稱，以及日期和時間的資訊建立和上次修改。

此程式碼會擷取為 Notepad.exe 的檔案資訊。

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

## <a name="write_binary"></a> 寫入二進位檔案

下列程式碼範例示範如何將二進位資料寫入檔案。 兩個類別<xref:System.IO>會使用命名空間：<xref:System.IO.FileStream>和<xref:System.IO.BinaryWriter>。 <xref:System.IO.FileStream> 表示實際的檔案，而<xref:System.IO.BinaryWriter>提供介面來進行二進位存取的資料流。

下列程式碼範例會寫入檔案，包含以二進位格式的整數。 可以讀取此檔案中的程式碼[如何： 讀取二進位檔案 (C + + /cli CLI)](../dotnet/how-to-read-a-binary-file-cpp-cli.md)。

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

## <a name="write_text"></a> 寫入文字檔

下列程式碼範例示範如何建立文字檔案，並將文字寫入至使用<xref:System.IO.StreamWriter>類別，其定義於<xref:System.IO>命名空間。 <xref:System.IO.StreamWriter>建構函式會採用要建立之檔案的名稱。 如果檔案存在，它會覆寫 (除非您傳遞 True 做為第二個<xref:System.IO.StringWriter>建構函式引數)。

檔案然後歸檔的方式使用<xref:System.IO.StreamWriter.Write%2A>和<xref:System.IO.TextWriter.WriteLine%2A>函式。

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

[以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

[檔案和資料流 I-O](/dotnet/standard/io/index)

[System.IO 命名空間](https://msdn.microsoft.com/library/system.io.aspx)