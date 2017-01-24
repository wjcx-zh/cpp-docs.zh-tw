---
title: "資料流 I/O | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.io"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "I/O [CRT], 資料流"
  - "I/O 常式, 資料流 I/O"
  - "資料流 I/O"
ms.assetid: dc7874d3-a91b-456a-9015-4748bb358217
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 資料流 I/O
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這些函式會處理不同大小和格式的資料，範圍從單一字元到大型資料結構。 它們也提供緩衝處理，如此可改善效能。 資料流緩衝區的預設大小是 4K。 這些常式只會影響執行階段程式庫常式所建立的緩衝區，而且不會影響作業系統所建立的緩衝區。  
  
### 資料流 I\/O 常式  
  
|常式|用法|.NET Framework 同等|  
|--------|--------|-----------------------|  
|[clearerr](../c-runtime-library/reference/clearerr.md) \([clearerr\_s](../c-runtime-library/reference/clearerr-s.md)\)|清除資料流的錯誤指標|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[fclose](../c-runtime-library/reference/fclose-fcloseall.md)|關閉資料流|[System::IO::Stream::Close](https://msdn.microsoft.com/en-us/library/system.io.stream.close.aspx)、[System::IO::BinaryReader::Close](https://msdn.microsoft.com/en-us/library/system.io.binaryreader.close.aspx)、[System::IO::BinaryWriter::Close](https://msdn.microsoft.com/en-us/library/system.io.binarywriter.close.aspx)、[System::IO::TextReader::Close](https://msdn.microsoft.com/en-us/library/system.io.textreader.close.aspx)、[System::IO::TextWriter::Close](https://msdn.microsoft.com/en-us/library/system.io.textwriter.close.aspx)、[System::IO::StringReader::Close](https://msdn.microsoft.com/en-us/library/system.io.stringreader.close.aspx)、[System::IO::StringWriter::Close](https://msdn.microsoft.com/en-us/library/system.io.stringwriter.close.aspx)、[System::IO::StreamReader::Close](https://msdn.microsoft.com/en-us/library/system.io.streamreader.close.aspx)、[System::IO::StreamWriter::Close](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.close.aspx)|  
|[\_fcloseall](../c-runtime-library/reference/fclose-fcloseall.md)|關閉所有開啟的資料流，但 `stdin`、`stdout` 和 `stderr` 除外|[System::IO::Stream::Close](https://msdn.microsoft.com/en-us/library/system.io.stream.close.aspx)、[System::IO::BinaryReader::Close](https://msdn.microsoft.com/en-us/library/system.io.binaryreader.close.aspx)、[System::IO::BinaryWriter::Close](https://msdn.microsoft.com/en-us/library/system.io.binarywriter.close.aspx)、[System::IO::TextReader::Close](https://msdn.microsoft.com/en-us/library/system.io.textreader.close.aspx)、[System::IO::TextWriter::Close](https://msdn.microsoft.com/en-us/library/system.io.textwriter.close.aspx)、[System::IO::StringReader::Close](https://msdn.microsoft.com/en-us/library/system.io.stringreader.close.aspx)、[System::IO::StringWriter::Close](https://msdn.microsoft.com/en-us/library/system.io.stringwriter.close.aspx)、[System::IO::StreamReader::Close](https://msdn.microsoft.com/en-us/library/system.io.streamreader.close.aspx)、[System::IO::StreamWriter::Close](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.close.aspx)|  
|[\_fdopen、wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)|關聯資料流與已開啟檔案的檔案描述項|<xref:System.IO.FileStream.%23ctor%2A>|  
|[feof](../c-runtime-library/reference/feof.md)|測試資料流上的檔案結尾|[System::IO::FileStream::Read](https://msdn.microsoft.com/en-us/library/system.io.filestream.read.aspx)|  
|[ferror](../c-runtime-library/reference/ferror.md)|測試資料流上的錯誤|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[fflush](../c-runtime-library/reference/fflush.md)|將資料流清除至緩衝區或存放裝置|[System::IO::FileStream::Flush](https://msdn.microsoft.com/en-us/library/2bw4h516.aspx)|  
|[fgetc、fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md)|從資料流讀取字元 \(`getc` 和 `getwc` 的函式版本\)|[System::IO::StreamReader::Read](https://msdn.microsoft.com/en-us/library/system.io.streamreader.read.aspx)|  
|[\_fgetchar、\_fgetwchar](../c-runtime-library/reference/fgetc-fgetwc.md)|從 `stdin` 讀取字元 \(`getchar` 和 `getwchar` 的函式版本\)|[System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx)|  
|[fgetpos](../c-runtime-library/reference/fgetpos.md)|取得資料流的位置指標|[System::IO::FileStream::Position](https://msdn.microsoft.com/en-us/library/system.io.filestream.position.aspx)|  
|[fgets、fgetws](../c-runtime-library/reference/fgets-fgetws.md)|從資料流讀取字串|[System::IO::StreamReader::ReadLine](https://msdn.microsoft.com/en-us/library/system.io.streamreader.readline.aspx)、[System::IO::TextReader::ReadBlock](https://msdn.microsoft.com/en-us/library/system.io.textreader.readblock.aspx)|  
|[\_fileno](../c-runtime-library/reference/fileno.md)|取得與資料流相關聯的檔案描述項|[System::IO::FileStream::Handle](https://msdn.microsoft.com/en-us/library/system.io.filestream.handle.aspx)|  
|[\_flushall](../c-runtime-library/reference/flushall.md)|將所有資料流清除至緩衝區或存放裝置|[System::IO::FileStream::Flush](https://msdn.microsoft.com/en-us/library/2bw4h516.aspx)、[System::IO::StreamWriter::Flush](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.flush.aspx)、[System::IO::TextWriter::Flush](https://msdn.microsoft.com/en-us/library/system.io.textwriter.flush.aspx)、[System::IO::BinaryWriter::Flush](https://msdn.microsoft.com/en-us/library/system.io.binarywriter.flush.aspx)|  
|[fopen, \_wfopen](../c-runtime-library/reference/fopen-wfopen.md)、[fopen\_s、\_wfopen\_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)|開啟資料流|[System::IO::File::Open](https://msdn.microsoft.com/en-us/library/system.io.file.open.aspx)|  
|[fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md), [fprintf\_s、\_fprintf\_s\_l、fwprintf\_s、\_fwprintf\_s\_l](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|將格式化資料寫入資料流|[System::IO::StreamWriter::Write](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.write.aspx)|  
|[fputc、fputwc](../c-runtime-library/reference/fputc-fputwc.md)|將字元寫入資料流 \(`putc` 和 `putwc` 的函式版本\)|[System::IO::StreamWriter::Write](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.write.aspx)|  
|[\_fputchar、\_fputwchar](../c-runtime-library/reference/fputc-fputwc.md)|將字元寫入 `stdout` \(`putchar` 和 `putwchar` 的函式版本\)|[System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)|  
|[fputs、fputws](../c-runtime-library/reference/fputs-fputws.md)|將字串寫入資料流|[System::IO::StreamWriter::Write](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.write.aspx)|  
|[fread](../c-runtime-library/reference/fread.md)|從資料流讀取未格式化資料|[System::IO::FileStream::Read](https://msdn.microsoft.com/en-us/library/system.io.filestream.read.aspx)|  
|[freopen、\_wfreopen](../c-runtime-library/reference/freopen-wfreopen.md) \([freopen\_s、\_wfreopen\_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)\)|將 `FILE` 資料流指標重新指派給新的檔案或裝置|[System::IO::File::Open](https://msdn.microsoft.com/en-us/library/system.io.file.open.aspx)|  
|[fscanf、fwscanf](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)、[fscanf\_s、\_fscanf\_s\_l、fwscanf\_s、\_fwscanf\_s\_l](../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)|從資料流讀取格式化資料|[System::IO::StreamReader::ReadLine](https://msdn.microsoft.com/en-us/library/system.io.streamreader.readline.aspx)；另請參閱 `Parse` 方法，例如 [System::Double::Parse](https://msdn.microsoft.com/en-us/library/system.double.parse.aspx)。|  
|[fseek、\_fseeki64](../c-runtime-library/reference/fseek-fseeki64.md)|將檔案位置移至指定的位置|[System::IO::FileStream::Position](https://msdn.microsoft.com/en-us/library/system.io.filestream.position.aspx)、[System::IO::FileStream::Seek](https://msdn.microsoft.com/en-us/library/system.io.filestream.seek.aspx)|  
|[fsetpos](../c-runtime-library/reference/fsetpos.md)|設定資料流的位置指標|[System::IO::FileStream::Position](https://msdn.microsoft.com/en-us/library/system.io.filestream.position.aspx)|  
|[\_fsopen、\_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)|以檔案共用開啟資料流|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[ftell、\_ftelli64](../c-runtime-library/reference/ftell-ftelli64.md)|取得目前檔案位置|[System::IO::FileStream::Position](https://msdn.microsoft.com/en-us/library/system.io.filestream.position.aspx)|  
|[fwrite](../c-runtime-library/reference/fwrite.md)|將未格式化資料項目寫入資料流|[System::IO::FileStream::Write](https://msdn.microsoft.com/en-us/library/system.io.filestream.write.aspx)|  
|[getc、getwc](../c-runtime-library/reference/getc-getwc.md)|從資料流讀取字元 \(`fgetc` 和 `fgetwc` 的巨集版本\)|[System::IO::StreamReader::Read](https://msdn.microsoft.com/en-us/library/system.io.streamreader.read.aspx)|  
|[getchar、getwchar](../c-runtime-library/reference/getc-getwc.md)|從 `stdin` 讀取字元 \(`fgetchar` 和 `fgetwchar` 的巨集版本\)|[System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx)|  
|[\_getmaxstdio](../c-runtime-library/reference/getmaxstdio.md)|傳回允許在資料流 I\/O 層級同時開啟的檔案數目。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[gets\_s、\_getws\_s](../c-runtime-library/reference/gets-s-getws-s.md)|從 `stdin` 讀取行|[System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx)|  
|[\_getw](../c-runtime-library/reference/getw.md)|從資料流讀取二進位 `int`|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[printf、\_printf\_l、wprintf、\_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)、[printf\_s、\_printf\_s\_l、wprintf\_s、\_wprintf\_s\_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|將格式化資料寫入 `stdout`|[System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)|  
|[putc、putwc](../c-runtime-library/reference/putc-putwc.md)|將字元寫入資料流 \(`fputc` 和 `fputwc` 的巨集版本\)|[System::IO::StreamWriter::Write](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.write.aspx)|  
|[putchar、putwchar](../c-runtime-library/reference/putc-putwc.md)|將字元寫入 `stdout` \(`fputchar` 和 `fputwchar` 的巨集版本\)|[System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)|  
|[puts、\_putws](../c-runtime-library/reference/puts-putws.md)|將行寫入資料流|[System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)|  
|[\_putw](../c-runtime-library/reference/putw.md)|將二進位 `int` 寫入資料流|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[rewind](../c-runtime-library/reference/rewind.md)|將檔案位置移至資料流開頭|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_rmtmp](../c-runtime-library/reference/rmtmp.md)|移除 `tmpfile` 所建立的暫存檔案|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[scanf、\_scanf\_l、wscanf、\_wscanf\_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)、[scanf\_s、\_scanf\_s\_l、wscanf\_s、\_wscanf\_s\_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)|從 `stdin` 讀取格式化資料|[System::Console::ReadLine](https://msdn.microsoft.com/en-us/library/system.console.readline.aspx)；另請參閱 `Parse` 方法，例如 [System::Double::Parse](https://msdn.microsoft.com/en-us/library/system.double.parse.aspx)。|  
|[setbuf](../c-runtime-library/reference/setbuf.md)|控制資料流緩衝|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md)|設定在資料流 I\/O 層級同時開啟的檔案數目上限。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[setvbuf](../c-runtime-library/reference/setvbuf.md)|控制資料流緩衝和緩衝區大小|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_snprintf、\_snwprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) \([\_snprintf\_s、\_snprintf\_s\_l、\_snwprintf\_s、\_snwprintf\_s\_l](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)\)|將所指定長度的格式化資料寫入字串|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_snscanf、\_snwscanf](../c-runtime-library/reference/snscanf-snscanf-l-snwscanf-snwscanf-l.md) \([\_snscanf\_s、\_snscanf\_s\_l、\_snwscanf\_s、\_snwscanf\_s\_l](../c-runtime-library/reference/snscanf-s-snscanf-s-l-snwscanf-s-snwscanf-s-l.md)\)|從標準輸入資料流讀取所指定長度的格式化資料。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[sprintf、swprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) \([sprintf\_s、\_sprintf\_s\_l、swprintf\_s、\_swprintf\_s\_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)\)|將格式化資料寫入字串|[System::String::Format](https://msdn.microsoft.com/en-us/library/system.string.format.aspx)|  
|[sscanf、swscanf](../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md) \([sscanf\_s、\_sscanf\_s\_l、swscanf\_s、\_swscanf\_s\_l](../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)\)|從字串讀取格式化資料|請參閱 `Parse` 方法，例如 [System::Double::Parse](https://msdn.microsoft.com/en-us/library/system.double.parse.aspx)|  
|[\_tempnam、\_wtempnam](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|在指定的目錄中產生暫存檔名|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[tmpfile](../c-runtime-library/reference/tmpfile.md) \([tmpfile\_s](../c-runtime-library/reference/tmpfile-s.md)\)|建立暫存檔|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[tmpnam、\_wtmpnam](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) \([tmpnam\_s、\_wtmpnam\_s](../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md)\)|產生暫存檔名|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[ungetc、ungetwc](../c-runtime-library/reference/ungetc-ungetwc.md)|將字元推送回資料流|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_vcprintf、\_vcwprintf](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md) \([\_vcprintf\_s、\_vcprintf\_s\_l、\_vcwprintf\_s、\_vcwprintf\_s\_l](../c-runtime-library/reference/vcprintf-s-vcprintf-s-l-vcwprintf-s-vcwprintf-s-l.md)\)|將格式化資料寫入主控台。|[System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)|  
|[vfprintf、vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md) \([vfprintf\_s、\_vfprintf\_s\_l、vfwprintf\_s、\_vfwprintf\_s\_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)\)|將格式化資料寫入資料流|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[vprintf、vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md) \([vprintf\_s、\_vprintf\_s\_l、vwprintf\_s、\_vwprintf\_s\_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)\)|將格式化資料寫入 `stdout`|[System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)|  
|[\_vsnprintf、\_vsnwprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) \([vsnprintf\_s、\_vsnprintf\_s、\_vsnprintf\_s\_l、\_vsnwprintf\_s、\_vsnwprintf\_s\_l](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)\)|將所指定長度的格式化資料寫入緩衝區|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[vsprintf、vswprintf](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md) \([vsprintf\_s、\_vsprintf\_s\_l、vswprintf\_s、\_vswprintf\_s\_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)\)|將格式化資料寫入緩衝區|[System::String::Format](https://msdn.microsoft.com/en-us/library/system.string.format.aspx)|  
  
 程式開始執行時，啟動程式碼會自動開啟數個資料流：標準輸入 \(由 `stdin` 指向\)、標準輸出 \(由 `stdout` 指向\) 和標準誤差 \(由 `stderr` 指向\)。 預設會將這些資料流導向主控台 \(鍵盤和螢幕\)。 使用 `freopen` 將 `stdin`、`stdout` 或 `stderr` 重新導向磁碟檔案或裝置。  
  
 預設會緩衝處理使用資料流常式所開啟的檔案。 在每次程式庫呼叫之後，`stdout` 和 `stderr` 函式只有在填滿或您撰寫至字元裝置時才會予以清除。 如果程式異常終止，則可能未清除輸出緩衝區，導致資料遺失。 使用 `fflush` 或 `_flushall` 確保與所指定檔案相關聯的緩衝區或是所有開啟的緩衝區都已清除至作業系統，這樣可以在寫入磁碟之前快取資料。 認可至磁碟功能確保清除的緩衝區內容不會在系統失敗時遺失。  
  
 有兩種方式可以將緩衝區內容認可至磁碟：  
  
-   使用檔案 COMMODE.OBJ 進行連結，以設定全域認可旗標。 全域旗標的預設設定是 `n` \(表示「不認可」\)。  
  
-   使用 `fopen` 或 `_fdopen`，將模式旗標設為 `c`。  
  
 不論全域認可\/不認可旗標的狀態為何，特別使用 `c` 或 `n` 旗標所開啟的任何檔案都是根據旗標所運作。  
  
 如果您的程式未明確地關閉資料流，則會在程式終止時自動關閉資料流。 不過，您應該在程式完成資料流的處理時關閉資料流，因為一次可以開啟的資料流數目有限。 如需這項限制的相關資訊，請參閱 [\_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md)。  
  
 只有在具有 `fflush` 或是檔案定位函式 \(`fseek`、`fsetpos` 或 `rewind`\) 的中間呼叫時，輸入才能直接遵循輸出。 如果輸入作業遇到檔案結尾，則輸出可以遵循輸入，而沒有檔案定位函式的中間呼叫。  
  
## 請參閱  
 [輸入和輸出](../c-runtime-library/input-and-output.md)   
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)