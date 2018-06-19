---
title: ATL 公用程式參考 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: dd8a2888-34f4-461e-9bf4-834218f9b95b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9b802d8764dda321e2e313f793f4f2e4745dbcc7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363819"
---
# <a name="atl-utilities-reference"></a>ATL 公用程式參考
ATL 提供程式碼操作的路徑和 Url 的形式[CPathT](../atl/reference/cpatht-class.md)和[CUrl](../atl/reference/curl-class.md)。 執行緒集區[CThreadPool](../atl/reference/cthreadpool-class.md)，可用於您的應用程式。 Atlpath.h 和 atlutil.h 中可以找到此程式碼。  
  
### <a name="classes"></a>類別  
  
|||  
|-|-|  
|[CPathT 類別](../atl/reference/cpatht-class.md)|此類別代表的路徑。|  
|[CDebugReportHook 類別](../atl/reference/cdebugreporthook-class.md)|使用此類別將偵錯報表傳送至具名的管道。|  
|[CNonStatelessWorker 類別](../atl/reference/cnonstatelessworker-class.md)|從執行緒集區接收要求，並將它們傳遞到會建立並終結背景工作物件中，每個要求。|  
|[CNoWorkerThread 類別](../atl/reference/cnoworkerthread-class.md)|使用此類別做為引數`MonitorClass`樣板參數，如果您想要停用動態快取維護的快取類別。|  
|[CThreadPool 類別](../atl/reference/cthreadpool-class.md)|這個類別會提供處理的工作項目佇列的背景工作執行緒集區。|  
|[CUrl 類別](../atl/reference/curl-class.md)|這個類別表示的 URL。 它可讓您操作各自 URL 的每個項目是否剖析現有的 URL 字串，或建置全新的字串。|  
|[CWorkerThread 類別](../atl/reference/cworkerthread-class.md)|這個類別建立背景工作執行緒或使用現有，等候一或多個核心物件控點，而且其中一個控點會收到信號時，執行指定的用戶端函式。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[CPath](../atl/reference/atl-typedefs.md#cpath)|特製化[CPathT](../atl/reference/cpatht-class.md)使用`CString`。|  
|[CPathA](../atl/reference/atl-typedefs.md#cpatha)|特製化[CPathT](../atl/reference/cpatht-class.md)使用`CStringA`。|  
|[CPathW](../atl/reference/atl-typedefs.md#cpathw)|特製化[CPathT](../atl/reference/cpatht-class.md)使用`CStringW`。|  
|[ATL_URL_PORT](../atl/reference/atl-typedefs.md#atl_url_port)|所使用的類型[CUrl](../atl/reference/curl-class.md)來指定連接埠號碼。|  
  
### <a name="enums"></a>列舉  
  
|||  
|-|-|  
|[ATL_URL_SCHEME](../atl/reference/atl-url-scheme-enum.md)|這個列舉的成員提供常數所了解配置[CUrl](../atl/reference/curl-class.md)。|  
  
### <a name="functions"></a>函式  
  
|||  
|-|-|  
|[AtlCanonicalizeUrl](../atl/reference/atl-http-utility-functions.md#atlcanonicalizeurl)|呼叫此函式可規範化 URL，包括將 Unsafe 字元和空格轉換成逸出序列。|  
|[AtlCombineUrl](../atl/reference/atl-http-utility-functions.md#atlcombineurl)|呼叫此函式可將基底 URL 和相對 URL 結合成單一、標準的 URL。|  
|[AtlEscapeUrl](../atl/reference/atl-http-utility-functions.md#atlescapeurl)|呼叫此函式會將所有 Unsafe 字元轉換成逸出序列。|  
|[AtlGetDefaultUrlPort](../atl/reference/atl-http-utility-functions.md#atlgetdefaulturlport)|呼叫此函式可取得與特定網際網路通訊協定或配置相關聯的預設通訊埠編號。|  
|[AtlHexValue](../atl/reference/atl-text-encoding-functions.md#atlhexvalue)|呼叫此函式可取得十六進位的數值。|  
|[AtlIsUnsafeUrlChar](../atl/reference/atl-http-utility-functions.md#atlisunsafeurlchar)|呼叫此函式可了解在 URL 中使用某個字元是否安全。|  
|[AtlUnescapeUrl](../atl/reference/atl-http-utility-functions.md#atlunescapeurl)|呼叫此函式將逸出字元轉換回其原始值。|  
|[SystemTimeToHttpDate](../atl/reference/atl-http-utility-functions.md#systemtimetohttpdate)|呼叫此函式將系統時間轉換成採用適合在 HTTP 標頭中使用之格式的字串。|  

|[ATLPath::AddBackslash](../atl/reference/atl-path-functions.md#addbackslash)|此函式是多載包裝函式[PathAddBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773561)。 |  
|[ATLPath::AddExtension](../atl/reference/atl-path-functions.md#addextension)|此函式是多載包裝函式[PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563)。 |  
|[ATLPath::Append](../atl/reference/atl-path-functions.md#append)|此函式是多載包裝函式[PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565)。 |  
|[ATLPath::BuildRoot](../atl/reference/atl-path-functions.md#buildroot)|此函式是多載包裝函式[PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567)。 |  
|[ATLPath::Canonicalize](../atl/reference/atl-path-functions.md#canonicalize)|此函式是多載包裝函式[PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569)。 |  
|[ATLPath::Combine](../atl/reference/atl-path-functions.md#combine)|此函式是多載包裝函式[PathCombine](http://msdn.microsoft.com/library/windows/desktop/bb773571)。 |  
|[ATLPath::CommonPrefix](../atl/reference/atl-path-functions.md#commonprefix)|此函式是多載包裝函式[PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574)。 |  
|[ATLPath::CompactPath](../atl/reference/atl-path-functions.md#compactpath)|此函式是多載包裝函式[PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575)。 |  
|[ATLPath::CompactPathEx](../atl/reference/atl-path-functions.md#compactpathex)|此函式是多載包裝函式[PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578)。 |  
|[ATLPath::FileExists](../atl/reference/atl-path-functions.md#fileexists)|此函式是多載包裝函式[PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584)。 |  
|[ATLPath::FindExtension](../atl/reference/atl-path-functions.md#findextension)|此函式是多載包裝函式[PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587)。 |  
|[ATLPath::FindFileName](../atl/reference/atl-path-functions.md#findfilename)|此函式是多載包裝函式[PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589)。 |  
|[ATLPath::GetDriveNumber](../atl/reference/atl-path-functions.md#getdrivenumber)|此函式是多載包裝函式[PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612)。 |  
|[ATLPath::IsDirectory](../atl/reference/atl-path-functions.md#isdirectory)|此函式是多載包裝函式[PathIsDirectory](http://msdn.microsoft.com/library/windows/desktop/bb773621)。 |  
|[ATLPath::IsFileSpec](../atl/reference/atl-path-functions.md#isfilespec)|此函式是多載包裝函式[PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627)。 |  
|[ATLPath::IsPrefix](../atl/reference/atl-path-functions.md#isprefix)|此函式是多載包裝函式[PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650)。 |  
|[ATLPath::IsRelative](../atl/reference/atl-path-functions.md#isrelative)|此函式是多載包裝函式[PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660)。 |  
|[ATLPath::IsRoot](../atl/reference/atl-path-functions.md#isroot)|此函式是多載包裝函式[PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674)。 |  
|[ATLPath::IsSameRoot](../atl/reference/atl-path-functions.md#issameroot)|此函式是多載包裝函式[PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687)。 |  
|[ATLPath::IsUNC](../atl/reference/atl-path-functions.md#isunc)|此函式是多載包裝函式[PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712)。 |  
|[ATLPath::IsUNCServer](../atl/reference/atl-path-functions.md#isuncserver)|此函式是多載包裝函式[PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722)。 |  
|[ATLPath::IsUNCServerShare](../atl/reference/atl-path-functions.md#isuncservershare)|此函式是多載包裝函式[PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723)。 |  
|[ATLPath::MakePretty](../atl/reference/atl-path-functions.md#makepretty)|此函式是多載包裝函式[PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725)。 |  
|[ATLPath::MatchSpec](../atl/reference/atl-path-functions.md#matchspec)|此函式是多載包裝函式[PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727)。 |  
|[ATLPath::QuoteSpaces](../atl/reference/atl-path-functions.md#quotespaces)|此函式是多載包裝函式[PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739)。 |  
|[ATLPath::RelativePathTo](../atl/reference/atl-path-functions.md#relativepathto)|此函式是多載包裝函式[PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740)。 |  
|[ATLPath::RemoveArgs](../atl/reference/atl-path-functions.md#removeargs)|此函式是多載包裝函式[PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742)。 |  
|[ATLPath::RemoveBackslash](../atl/reference/atl-path-functions.md#removebackslash)|此函式是多載包裝函式[PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743)。 |  
|[ATLPath::RemoveBlanks](../atl/reference/atl-path-functions.md#removeblanks)|此函式是多載包裝函式[PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745)。 |  
|[ATLPath::RemoveExtension](../atl/reference/atl-path-functions.md#removeextension)|此函式是多載包裝函式[PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746)。 |  
|[ATLPath::RemoveFileSpec](../atl/reference/atl-path-functions.md#removefilespec)|此函式是多載包裝函式[PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748)。 |  
|[ATLPath::RenameExtension](../atl/reference/atl-path-functions.md#renameextension)|此函式是多載包裝函式[PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749)。 |  
|[ATLPath::SkipRoot](../atl/reference/atl-path-functions.md#skiproot)|此函式是多載包裝函式[PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754)。 |  
|[ATLPath::StripPath](../atl/reference/atl-path-functions.md#strippath)|此函式是多載包裝函式[PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756)。 |  
|[ATLPath::StripToRoot](../atl/reference/atl-path-functions.md#striptoroot)|此函式是多載包裝函式[PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757)。 |  
|[ATLPath::UnquoteSpaces](../atl/reference/atl-path-functions.md#unquotespaces)|此函式是多載包裝函式[PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763)。 |  
  

## <a name="see-also"></a>另請參閱  
 [概念](../atl/active-template-library-atl-concepts.md)   
 [ATL COM 桌面元件](../atl/atl-com-desktop-components.md)
