---
title: "ATL 公用程式參考 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: dd8a2888-34f4-461e-9bf4-834218f9b95b
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# ATL 公用程式參考
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

以 [CPathT](../atl/reference/cpatht-class.md) 和 [卷毛](../atl/reference/curl-class.md)的形式， ATL 提供管理的路徑和 URL 的程式碼。  執行緒集區， [CThreadPool](../atl/reference/cthreadpool-class.md)，可用於應用程式。  這個程式碼可以在類別和函式找到。  
  
### 類別  
  
|||  
|-|-|  
|[CPathT 類別](../atl/reference/cpatht-class.md)|這個類別表示路徑。|  
|[CDebugReportHook 類別](../atl/reference/cdebugreporthook-class.md)|使用這個類別會將偵錯回報給具名管道。|  
|[CNonStatelessWorker 類別](../atl/reference/cnonstatelessworker-class.md)|取得從執行緒集區的要求並傳遞至在每個要求都會建立並終結的工作物件。|  
|[CNoWorkerThread 類別](../atl/reference/cnoworkerthread-class.md)|如果您想要停用動態快取中維護，請使用這個類別做為引數才能 `MonitorClass` 樣板參數可以快取類別。|  
|[CThreadPool 類別](../atl/reference/cthreadpool-class.md)|這個類別會提供處理工作項目佇列的背景工作執行緒集區。|  
|[卷毛類別](../atl/reference/curl-class.md)|這個類別表示 URL。  它是否可以讓您獨立作業 URL 的每個項目會剖析現有的 URL 字串或從頭建置字串。|  
|[CWorkerThread 類別](../atl/reference/cworkerthread-class.md)|當其中一個控制代碼都收到信號時，這個類別會在一或多個核心物件控制代碼建立背景工作執行緒或使用現有的平台，等待，並執行指定的用戶端函式。|  
  
### Typedef  
  
|||  
|-|-|  
|[CPath](../Topic/CPath.md)|[CPathT](../atl/reference/cpatht-class.md) 的特製化使用 `CString`的。|  
|[CPathA](../Topic/CPathA.md)|[CPathT](../atl/reference/cpatht-class.md) 的特製化使用 `CStringA`的。|  
|[CPathW](../Topic/CPathW.md)|[CPathT](../atl/reference/cpatht-class.md) 的特製化使用 `CStringW`的。|  
|[ATL\_URL\_PORT](../Topic/ATL_URL_PORT.md)|[卷毛](../atl/reference/curl-class.md) 使用的型別用於指定通訊埠編號。|  
  
### 列舉  
  
|||  
|-|-|  
|[ATL\_URL\_SCHEME](../Topic/ATL_URL_SCHEME.md)|這個列舉型別的成員。 [卷毛](../atl/reference/curl-class.md)了解配置提供常數。|  
  
### 功能  
  
|||  
|-|-|  
|[AtlCanonicalizeUrl](../Topic/AtlCanonicalizeUrl.md)|呼叫此函式規範化 URL，包括轉換不安全的字元和空白字元的逸出序列 \(Escape Sequence\)。|  
|[AtlCombineUrl](../Topic/AtlCombineUrl.md)|呼叫此函式結合基底 URL 和相對 URL 輸入單一，標準 URL。|  
|[AtlEscapeUrl](../Topic/AtlEscapeUrl.md)|呼叫此函式轉換所有不安全的字元為逸出序列 \(Escape Sequence\)。|  
|[AtlGetDefaultUrlPort](../Topic/AtlGetDefaultUrlPort.md)|呼叫此函式來取得預設通訊埠編號與特定網際網路通訊協定 \(IP\) 或計劃。|  
|[AtlHexValue](../Topic/AtlHexValue.md)|呼叫此函式來取得十六進位數字的數值。|  
|[AtlIsUnsafeUrlChar](../Topic/AtlIsUnsafeUrlChar.md)|呼叫這個函式尋找字元是否可安全地用於 URL。|  
|[AtlUnescapeUrl](../Topic/AtlUnescapeUrl.md)|呼叫此函式將轉換為逸出字元回其原始值。|  
|[SystemTimeToHttpDate](../Topic/SystemTimeToHttpDate.md)|呼叫此函式將一種系統時間設為適當的格式字串使用 HTTP 標頭。|  
|[ATLPath::AddBackslash](../Topic/ATLPath::AddBackslash.md)|這個函式是 [PathAddBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773561)的多載的包裝函式。|  
|[ATLPath::AddExtension](../Topic/ATLPath::AddExtension.md)|這個函式是 [PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563)的多載的包裝函式。|  
|[ATLPath::Append](../Topic/ATLPath::Append.md)|這個函式是 [PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565)的多載的包裝函式。|  
|[ATLPath::BuildRoot](../Topic/ATLPath::BuildRoot.md)|這個函式是 [PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567)的多載的包裝函式。|  
|[ATLPath::Canonicalize](../Topic/ATLPath::Canonicalize.md)|這個函式是 [PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569)的多載的包裝函式。|  
|[ATLPath::Combine](../Topic/ATLPath::Combine.md)|這個函式是 [PathCombine](http://msdn.microsoft.com/library/windows/desktop/bb773571)的多載的包裝函式。|  
|[ATLPath::CommonPrefix](../Topic/ATLPath::CommonPrefix.md)|這個函式是 [PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574)的多載的包裝函式。|  
|[ATLPath::CompactPath](../Topic/ATLPath::CompactPath.md)|這個函式是 [PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575)的多載的包裝函式。|  
|[ATLPath::CompactPathEx](../Topic/ATLPath::CompactPathEx.md)|這個函式是 [PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578)的多載的包裝函式。|  
|[ATLPath::FileExists](../Topic/ATLPath::FileExists.md)|這個函式是 [PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584)的多載的包裝函式。|  
|[ATLPath::FindExtension](../Topic/ATLPath::FindExtension.md)|這個函式是 [PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587)的多載的包裝函式。|  
|[ATLPath::FindFileName](../Topic/ATLPath::FindFileName.md)|這個函式是 [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589)的多載的包裝函式。|  
|[ATLPath::GetDriveNumber](../Topic/ATLPath::GetDriveNumber.md)|這個函式是 [PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612)的多載的包裝函式。|  
|[ATLPath::IsDirectory](../Topic/ATLPath::IsDirectory.md)|這個函式是 [PathIsDirectory](http://msdn.microsoft.com/library/windows/desktop/bb773621)的多載的包裝函式。|  
|[ATLPath::IsFileSpec](../Topic/ATLPath::IsFileSpec.md)|這個函式是 [PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627)的多載的包裝函式。|  
|[ATLPath::IsPrefix](../Topic/ATLPath::IsPrefix.md)|這個函式是 [PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650)的多載的包裝函式。|  
|[ATLPath::IsRelative](../Topic/ATLPath::IsRelative.md)|這個函式是 [PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660)的多載的包裝函式。|  
|[ATLPath::IsRoot](../Topic/ATLPath::IsRoot.md)|這個函式是 [PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674)的多載的包裝函式。|  
|[ATLPath::IsSameRoot](../Topic/ATLPath::IsSameRoot.md)|這個函式是 [PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687)的多載的包裝函式。|  
|[ATLPath::IsUNC](../Topic/ATLPath::IsUNC.md)|這個函式是 [PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712)的多載的包裝函式。|  
|[ATLPath::IsUNCServer](../Topic/ATLPath::IsUNCServer.md)|這個函式是 [PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722)的多載的包裝函式。|  
|[ATLPath::IsUNCServerShare](../Topic/ATLPath::IsUNCServerShare.md)|這個函式是 [PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723)的多載的包裝函式。|  
|[ATLPath::MakePretty](../Topic/ATLPath::MakePretty.md)|這個函式是 [PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725)的多載的包裝函式。|  
|[ATLPath::MatchSpec](../Topic/ATLPath::MatchSpec.md)|這個函式是 [PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727)的多載的包裝函式。|  
|[ATLPath::QuoteSpaces](../Topic/ATLPath::QuoteSpaces.md)|這個函式是 [PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739)的多載的包裝函式。|  
|[ATLPath::RelativePathTo](../Topic/ATLPath::RelativePathTo.md)|這個函式是 [PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740)的多載的包裝函式。|  
|[ATLPath::RemoveArgs](../Topic/ATLPath::RemoveArgs.md)|這個函式是 [PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742)的多載的包裝函式。|  
|[ATLPath::RemoveBackslash](../Topic/ATLPath::RemoveBackslash.md)|這個函式是 [PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743)的多載的包裝函式。|  
|[ATLPath::RemoveBlanks](../Topic/ATLPath::RemoveBlanks.md)|這個函式是 [PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745)的多載的包裝函式。|  
|[ATLPath::RemoveExtension](../Topic/ATLPath::RemoveExtension.md)|這個函式是 [PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746)的多載的包裝函式。|  
|[ATLPath::RemoveFileSpec](../Topic/ATLPath::RemoveFileSpec.md)|這個函式是 [PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748)的多載的包裝函式。|  
|[ATLPath::RenameExtension](../Topic/ATLPath::RenameExtension.md)|這個函式是 [PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749)的多載的包裝函式。|  
|[ATLPath::SkipRoot](../Topic/ATLPath::SkipRoot.md)|這個函式是 [PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754)的多載的包裝函式。|  
|[ATLPath::StripPath](../Topic/ATLPath::StripPath.md)|這個函式是 [PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756)的多載的包裝函式。|  
|[ATLPath::StripToRoot](../Topic/ATLPath::StripToRoot.md)|這個函式是 [PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757)的多載的包裝函式。|  
|[ATLPath::UnquoteSpaces](../Topic/ATLPath::UnquoteSpaces.md)|這個函式是 [PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763)的多載的包裝函式。|  
  
### 巨集  
  
|||  
|-|-|  
|[ATL\_URL 旗標。](../Topic/ATL_URL%20Flags.md)|這些旗標修改 [AtlEscapeUrl](../Topic/AtlEscapeUrl.md) 和 [AtlCanonicalizeUrl](../Topic/AtlCanonicalizeUrl.md) 行為。|  
|[ATL\_WORKER\_THREAD\_WAIT](../Topic/ATL_WORKER_THREAD_WAIT.md)|這個巨集以毫秒定義預設值 [CWorkerThread::Shutdown](../Topic/CWorkerThread::Shutdown.md) 等待背景工作執行緒關閉。|  
|[ATLS\_DEFAULT\_THREADPOOLSHUTDOWNTIMEOUT](../Topic/ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT.md)|這個巨集以毫秒定義預設時間 [CThreadPool](../atl/reference/cthreadpool-class.md) 會等候執行緒關閉。|  
|[ATLS\_DEFAULT\_THREADSPERPROC](../Topic/ATLS_DEFAULT_THREADSPERPROC.md)|這個巨集定義執行緒的預設數目每個 [CThreadPool](../atl/reference/cthreadpool-class.md)使用的處理器。|  
  
## 請參閱  
 [概念](../atl/active-template-library-atl-concepts.md)   
 [ATL COM Desktop Components](../atl/atl-com-desktop-components.md)