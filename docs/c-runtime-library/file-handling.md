---
title: "檔案處理 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.files
dev_langs:
- C++
helpviewer_keywords:
- files [C++], handling
- files [C++], opening
- files [C++], manipulating
ms.assetid: 48119e2e-e94f-4602-b08b-b72440f731d8
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 28ee6adcd86814d5804e0d9d34dd27a3c6d22f71

---
# <a name="file-handling"></a>檔案處理
使用這些常式以建立、刪除和管理檔案，並設定和檢查檔案存取權限。  
  
 C 執行階段程式庫同時開啟檔案數目的上限為 512。 嘗試開啟大於數目上限的檔案描述項或檔案資料流將導致程式發生錯誤。 請使用 [_setmaxstdio](../c-runtime-library/reference/setmaxstdio.md) 變更此數字。  
  
 下列常式會對檔案描述項所指定的檔案進行操作。  
  
### <a name="file-handling-routines-file-descriptor"></a>檔案處理常式 (檔案描述項)  
  
|常式|用法|.NET Framework 同等|  
|-------------|---------|-------------------------------|  
|[_chsize](../c-runtime-library/reference/chsize.md)、[_chsize_s](../c-runtime-library/reference/chsize-s.md)|變更檔案大小|[System::IO::Stream::SetLength](https://msdn.microsoft.com/en-us/library/system.io.stream.setlength.aspx)、 [System::IO::FileStream::SetLength](https://msdn.microsoft.com/en-us/library/system.io.filestream.setlength.aspx)|  
|[_filelength、_filelengthi64](../c-runtime-library/reference/filelength-filelengthi64.md)|取得檔案長度|[System::IO::Stream::Length](https://msdn.microsoft.com/en-us/library/system.io.stream.length.aspx)、 [System::IO::FileStream::Length](https://msdn.microsoft.com/en-us/library/system.io.filestream.length.aspx)|  
|[_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)|取得描述項的檔案狀態資訊|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_get_osfhandle](../c-runtime-library/reference/get-osfhandle.md)|傳回與現有 C 執行階段檔案描述項相關聯的作業系統檔案控制代碼|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_isatty](../c-runtime-library/reference/isatty.md)|檢查字元裝置|[System::IO::Stream::CanWrite](https://msdn.microsoft.com/en-us/library/system.io.filestream.canwrite.aspx)、 [System::IO::FileStream::CanWrite](https://msdn.microsoft.com/en-us/library/system.io.stream.canwrite.aspx)|  
|[_locking](../c-runtime-library/reference/locking.md)|檔案鎖定區域|[System::IO::FileStream::Lock](https://msdn.microsoft.com/en-us/library/system.io.filestream.lock.aspx)|  
|[_open_osfhandle](../c-runtime-library/reference/open-osfhandle.md)|將 C 執行階段檔案描述項與現有作業系統檔案控制代碼產生關聯|[System::IO::FileStream::Handle](https://msdn.microsoft.com/en-us/library/system.io.filestream.handle.aspx)|  
|[_setmode](../c-runtime-library/reference/setmode.md)|設定檔案轉譯模式|[System::IO::BinaryReader Class](https://msdn.microsoft.com/en-us/library/system.io.binaryreader.aspx)、 [System::IO::TextReader Class](https://msdn.microsoft.com/en-us/library/system.io.textreader.aspx)|  
  
 下列常式會對由路徑或檔名指定的檔案進行操作。  
  
### <a name="file-handling-routines-path-or-filename"></a>檔案處理常式 (路徑或檔案名稱)  
  
|常式|用法|.NET Framework 同等|  
|-------------|---------|-------------------------------|  
|[_access、_waccess](../c-runtime-library/reference/access-waccess.md) 以及 [_access_s、_waccess_s](../c-runtime-library/reference/access-s-waccess-s.md)|檢查檔案權限設定|[System::IO::FileAccess Enumeration](https://msdn.microsoft.com/en-us/library/4z36sx0f.aspx)|  
|[_chmod、_wchmod](../c-runtime-library/reference/chmod-wchmod.md)|變更檔案權限設定|[System::IO::File::SetAttributes](https://msdn.microsoft.com/en-us/library/system.io.file.setattributes.aspx)、 [System::Security::Permissions::FileIOPermission](https://msdn.microsoft.com/en-us/library/system.security.permissions.fileiopermission.aspx)|  
|[_fullpath、_wfullpath](../c-runtime-library/reference/fullpath-wfullpath.md)|將相對路徑展開為絕對路徑名稱|[System::IO::File::Create](https://msdn.microsoft.com/en-us/library/system.io.file.create.aspx)|  
|[_makepath、_wmakepath](../c-runtime-library/reference/makepath-wmakepath.md) 以及 [_makepath_s、_wmakepath_s](../c-runtime-library/reference/makepath-s-wmakepath-s.md)|將路徑元件合併成單一的完整路徑|[System::IO::File::Create](https://msdn.microsoft.com/en-us/library/system.io.file.create.aspx)|  
|[_mktemp、_wmktemp](../c-runtime-library/reference/mktemp-wmktemp.md) 以及 [_mktemp_s、_wmktemp_s](../c-runtime-library/reference/mktemp-s-wmktemp-s.md)|建立唯一的檔名|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[remove、_wremove](../c-runtime-library/reference/remove-wremove.md)|刪除檔案|[System::IO::File::Delete](https://msdn.microsoft.com/en-us/library/system.io.file.delete.aspx)|  
|[rename、_wrename](../c-runtime-library/reference/rename-wrename.md)|重新命名檔案|[System::IO::File::Move](https://msdn.microsoft.com/en-us/library/system.io.file.move.aspx)|  
|[_splitpath、_wsplitpath](../c-runtime-library/reference/splitpath-wsplitpath.md) 以及 [_splitpath_s、_wsplitpath_s](../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)|將路徑剖析成元件|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_stat、_stat64、_stati64、_wstat、_wstat64、_wstati64](../c-runtime-library/reference/stat-functions.md)|取得有關具名檔案的檔案狀態資訊|[System::IO::File::GetAttributes](https://msdn.microsoft.com/en-us/library/system.io.file.getattributes.aspx)、 [System::IO::File::GetCreationTime](https://msdn.microsoft.com/en-us/library/system.io.file.getcreationtime.aspx)、 [System::IO::File::GetLastAccessTime](https://msdn.microsoft.com/en-us/library/system.io.file.getlastaccesstime.aspx)、 [System::IO::File::GetLastWriteTime](https://msdn.microsoft.com/en-us/library/system.io.file.getlastwritetime.aspx)|  
|[_umask](../c-runtime-library/reference/umask.md)、[_umask_s](../c-runtime-library/reference/umask-s.md)|將程式建立的新檔案設定為預設權限遮罩|[System::IO::File::SetAttributes](https://msdn.microsoft.com/en-us/library/system.io.file.setattributes.aspx)|  
|[_unlink、_wunlink](../c-runtime-library/reference/unlink-wunlink.md)|刪除檔案|[System::IO::File::Delete](https://msdn.microsoft.com/en-us/library/system.io.file.delete.aspx)|  
  
 下列常式會開啟檔案。  
  
### <a name="file-handling-routines-open-file"></a>檔案處理常式 (開啟檔案)  
  
|常式|用法|.NET Framework 同等|  
|-------------|---------|-------------------------------|  
|[fopen、_wfopen](../c-runtime-library/reference/fopen-wfopen.md) 以及 [fopen_s、_wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)|開啟檔案並傳回此開啟檔案的指標。|[System::IO::File::Open](https://msdn.microsoft.com/en-us/library/system.io.file.open.aspx)，<xref:System.IO.FileStream.%23ctor%2A>|  
|[_fsopen、_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)|以檔案共用開啟資料流，並傳回此開啟檔案的指標。|[System::IO::File::Open](https://msdn.microsoft.com/en-us/library/system.io.file.open.aspx)，<xref:System.IO.FileStream.%23ctor%2A>|  
|[_open、_wopen](../c-runtime-library/reference/open-wopen.md)|開啟檔案，並傳回檔案描述項至已開啟的檔案。|[System::IO::File::Open](https://msdn.microsoft.com/en-us/library/system.io.file.open.aspx)，<xref:System.IO.FileStream.%23ctor%2A>|  
|[_sopen、_wsopen](../c-runtime-library/reference/sopen-wsopen.md) 以及 [_sopen_s、_wsopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)|以檔案共用開啟檔案，並傳回檔案描述項至該開啟檔案。||  
|[_pipe](../c-runtime-library/reference/pipe.md)|建立用於讀取和寫入的管道。|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[freopen、_wfreopen](../c-runtime-library/reference/freopen-wfreopen.md) 以及 [freopen_s、_wfreopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|重新指派檔案指標。|[System::IO::File::Open](https://msdn.microsoft.com/en-us/library/system.io.file.open.aspx)，<xref:System.IO.FileStream.%23ctor%2A>|  
  
 下列函式提供在 `FILE` 結構、檔案描述項和 Win32 檔案控制代碼之間變更檔案表示的方式。  
  
||||  
|-|-|-|  
|[_fdopen、_wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)|將資料流與先前針對低層級 I/O 開啟的檔案建立關聯，並傳回此開啟資料流的指標。|[System::IO::File::Open](https://msdn.microsoft.com/en-us/library/system.io.filestream.aspx)|  
|[_fileno](../c-runtime-library/reference/fileno.md)|取得與資料流相關聯的檔案描述項。|[System::IO::FileStream::Handle](https://msdn.microsoft.com/en-us/library/system.io.filestream.handle.aspx)|  
|[_get_osfhandle](../c-runtime-library/reference/get-osfhandle.md)|傳回與現有 C 執行階段檔案描述項相關聯的作業系統檔案控制代碼|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_open_osfhandle](../c-runtime-library/reference/open-osfhandle.md)|將現有作業系統檔案控制代碼與 C 執行階段檔案描述項建立關聯。|[System::IO::FileStream::Handle](https://msdn.microsoft.com/en-us/library/system.io.filestream.handle.aspx)|  
  
 下列的 Win32 函式也會開啟檔案和管道：  
  
-   [CreateFile](http://msdn.microsoft.com/library/windows/desktop/aa363858.aspx) (CreateFile 函式)  
  
-   [CreatePipe](http://msdn.microsoft.com/library/windows/desktop/aa365152.aspx) (CreatePipe 函式)  
  
-   [CreateNamedPipe](http://msdn.microsoft.com/library/windows/desktop/aa365150.aspx) (CreateNamedPipe 函式)  
  
## <a name="see-also"></a>另請參閱  
 [依類別區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)   
 [目錄控制](../c-runtime-library/directory-control.md)   
 [系統呼叫](../c-runtime-library/system-calls.md)


<!--HONumber=Feb17_HO4-->


