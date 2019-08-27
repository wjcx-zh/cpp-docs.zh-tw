---
title: ATL 公用程式參考
ms.date: 11/04/2016
ms.assetid: dd8a2888-34f4-461e-9bf4-834218f9b95b
ms.openlocfilehash: 6c1481929f832e6f810ce46773f328f278b503fa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491706"
---
# <a name="atl-utilities-reference"></a>ATL 公用程式參考

ATL 提供程式碼, 以[CPathT](../atl/reference/cpatht-class.md)和[捲曲](../atl/reference/curl-class.md)的形式操作路徑和 url。 執行緒集區[CThreadPool](../atl/reference/cthreadpool-class.md)可用於您的應用程式中。 此程式碼可以在 atlpath.h 和 atlutil.h 中找到。

### <a name="classes"></a>類別

|||
|-|-|
|[CPathT 類別](../atl/reference/cpatht-class.md)|此類別代表路徑。|
|[CDebugReportHook 類別](../atl/reference/cdebugreporthook-class.md)|使用這個類別, 即可將 debug 報表傳送到具名管道。|
|[CNonStatelessWorker 類別](../atl/reference/cnonstatelessworker-class.md)|接收來自執行緒集區的要求, 並將它們傳遞至在每個要求上建立和終結的背景工作物件。|
|[CNoWorkerThread 類別](../atl/reference/cnoworkerthread-class.md)|如果您想要停用動態快`MonitorClass`取維護, 請使用這個類別作為範本參數的引數來快取類別。|
|[CThreadPool 類別](../atl/reference/cthreadpool-class.md)|這個類別會提供可處理工作專案佇列的背景工作執行緒集區。|
|[CUrl 類別](../atl/reference/curl-class.md)|此類別代表 URL。 除了剖析現有的 URL 字串或從頭開始建立字串之外, 它還可讓您管理 URL 的每個專案, 而不受其他元素影響。|
|[CWorkerThread 類別](../atl/reference/cworkerthread-class.md)|這個類別會建立背景工作執行緒, 或使用現有的一個或多個核心物件控制碼, 並在其中一個控制碼收到信號時, 執行指定的用戶端函式。|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[CPath](../atl/reference/atl-typedefs.md#cpath)|使用`CString` [CPathT](../atl/reference/cpatht-class.md)的特製化。|
|[CPathA](../atl/reference/atl-typedefs.md#cpatha)|使用`CStringA` [CPathT](../atl/reference/cpatht-class.md)的特製化。|
|[CPathW](../atl/reference/atl-typedefs.md#cpathw)|使用`CStringW` [CPathT](../atl/reference/cpatht-class.md)的特製化。|
|[ATL_URL_PORT](../atl/reference/atl-typedefs.md#atl_url_port)|由[捲曲](../atl/reference/curl-class.md)用來指定埠號碼的類型。|

### <a name="enums"></a>列舉

|||
|-|-|
|[ATL_URL_SCHEME](../atl/reference/atl-url-scheme-enum.md)|此列舉的成員會針對[捲曲](../atl/reference/curl-class.md)所瞭解的配置提供常數。|

### <a name="functions"></a>函式

|||
|-|-|
|[AtlCanonicalizeUrl](../atl/reference/atl-http-utility-functions.md#atlcanonicalizeurl)|呼叫此函式可規範化 URL，包括將 Unsafe 字元和空格轉換成逸出序列。|
|[AtlCombineUrl](../atl/reference/atl-http-utility-functions.md#atlcombineurl)|呼叫此函式可將基底 URL 和相對 URL 結合成單一、標準的 URL。|
|[AtlEscapeUrl](../atl/reference/atl-http-utility-functions.md#atlescapeurl)|呼叫此函式會將所有 Unsafe 字元轉換成逸出序列。|
|[AtlGetDefaultUrlPort](../atl/reference/atl-http-utility-functions.md#atlgetdefaulturlport)|呼叫此函式可取得與特定網際網路通訊協定或配置相關聯的預設埠號碼。|
|[AtlHexValue](../atl/reference/atl-text-encoding-functions.md#atlhexvalue)|呼叫此函式可取得十六進位的數值。|
|[AtlIsUnsafeUrlChar](../atl/reference/atl-http-utility-functions.md#atlisunsafeurlchar)|呼叫此函式可了解在 URL 中使用某個字元是否安全。|
|[AtlUnescapeUrl](../atl/reference/atl-http-utility-functions.md#atlunescapeurl)|呼叫此函式將逸出字元轉換回其原始值。|
|[SystemTimeToHttpDate](../atl/reference/atl-http-utility-functions.md#systemtimetohttpdate)|呼叫此函式將系統時間轉換成採用適合在 HTTP 標頭中使用之格式的字串。|

|[ATLPath::AddBackslash](../atl/reference/atl-path-functions.md#addbackslash)|此函式是多載包裝函式[PathAddBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha
)。 | |[ATLPath::AddExtension](../atl/reference/atl-path-functions.md#addextension)|此函式是多載包裝函式[PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw)。 | |[ATLPath::Append](../atl/reference/atl-path-functions.md#append)|此函式是多載包裝函式[PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw)。 | |[ATLPath::BuildRoot](../atl/reference/atl-path-functions.md#buildroot)|此函式是多載包裝函式[PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw)。 | |[ATLPath::Canonicalize](../atl/reference/atl-path-functions.md#canonicalize)|此函式是多載包裝函式[PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew)。 | |[ATLPath::Combine](../atl/reference/atl-path-functions.md#combine)|此函式是多載包裝函式[PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew)。 | |[ATLPath::CommonPrefix](../atl/reference/atl-path-functions.md#commonprefix)|此函式是多載包裝函式[PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw)。 | |[ATLPath::CompactPath](../atl/reference/atl-path-functions.md#compactpath)|此函式是多載包裝函式[PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw)。 | |[ATLPath::CompactPathEx](../atl/reference/atl-path-functions.md#compactpathex)|此函式是多載包裝函式[PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw)。 | |[ATLPath::FileExists](../atl/reference/atl-path-functions.md#fileexists)|此函式是多載包裝函式[PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw)。 | |[ATLPath::FindExtension](../atl/reference/atl-path-functions.md#findextension)|此函式是多載包裝函式[PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw)。 | |[ATLPath::FindFileName](../atl/reference/atl-path-functions.md#findfilename)|此函式是多載包裝函式[PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)。 | |[ATLPath::GetDriveNumber](../atl/reference/atl-path-functions.md#getdrivenumber)|此函式是多載包裝函式[PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw)。 | |[ATLPath::IsDirectory](../atl/reference/atl-path-functions.md#isdirectory)|此函式是多載包裝函式[PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw)。 | |[ATLPath::IsFileSpec](../atl/reference/atl-path-functions.md#isfilespec)|此函式是多載包裝函式[PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw)。 | |[ATLPath::IsPrefix](../atl/reference/atl-path-functions.md#isprefix)|此函式是多載包裝函式[PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)。 | |[ATLPath::IsRelative](../atl/reference/atl-path-functions.md#isrelative)|此函式是多載包裝函式[PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew)。 | |[ATLPath::IsRoot](../atl/reference/atl-path-functions.md#isroot)|此函式是多載包裝函式[PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw)。 | |[ATLPath::IsSameRoot](../atl/reference/atl-path-functions.md#issameroot)|此函式是多載包裝函式[PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw)。 | |[ATLPath::IsUNC](../atl/reference/atl-path-functions.md#isunc)|此函式是多載包裝函式[PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw)。 | |[ATLPath::IsUNCServer](../atl/reference/atl-path-functions.md#isuncserver)|此函式是多載包裝函式[PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw)。 | |[ATLPath::IsUNCServerShare](../atl/reference/atl-path-functions.md#isuncservershare)|此函式是多載包裝函式[PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).| |[ATLPath::MakePretty](../atl/reference/atl-path-functions.md#makepretty)|This function is an overloaded wrapper for [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).| |[ATLPath::MatchSpec](../atl/reference/atl-path-functions.md#matchspec)|This function is an overloaded wrapper for [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).| |[ATLPath::QuoteSpaces](../atl/reference/atl-path-functions.md#quotespaces)|This function is an overloaded wrapper for [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).| |[ATLPath::RelativePathTo](../atl/reference/atl-path-functions.md#relativepathto)|This function is an overloaded wrapper for [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).| |[ATLPath::RemoveArgs](../atl/reference/atl-path-functions.md#removeargs)|This function is an overloaded wrapper for [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw).| |[ATLPath::RemoveBackslash](../atl/reference/atl-path-functions.md#removebackslash)|This function is an overloaded wrapper for [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw).| |[ATLPath::RemoveBlanks](../atl/reference/atl-path-functions.md#removeblanks)|This function is an overloaded wrapper for [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw).| |[ATLPath::RemoveExtension](../atl/reference/atl-path-functions.md#removeextension)|This function is an overloaded wrapper for [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw).| |[ATLPath::RemoveFileSpec](../atl/reference/atl-path-functions.md#removefilespec)|This function is an overloaded wrapper for [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw).| |[ATLPath::RenameExtension](../atl/reference/atl-path-functions.md#renameextension)|This function is an overloaded wrapper for [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).| |[ATLPath::SkipRoot](../atl/reference/atl-path-functions.md#skiproot)|This function is an overloaded wrapper for [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).| |[ATLPath::StripPath](../atl/reference/atl-path-functions.md#strippath)|This function is an overloaded wrapper for [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).| |[ATLPath::StripToRoot](../atl/reference/atl-path-functions.md#striptoroot)|This function is an overloaded wrapper for [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).| |[ATLPath::UnquoteSpaces](../atl/reference/atl-path-functions.md#unquotespaces)|This function is an overloaded wrapper for [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).|

## <a name="see-also"></a>另請參閱

[概念](../atl/active-template-library-atl-concepts.md)<br/>
[ATL COM 桌面元件](../atl/atl-com-desktop-components.md)
