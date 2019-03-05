---
title: ATL 公用程式參考
ms.date: 11/04/2016
ms.assetid: dd8a2888-34f4-461e-9bf4-834218f9b95b
ms.openlocfilehash: b5365ddc2924955fbdcf694065c4d4041a38eb01
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271940"
---
# <a name="atl-utilities-reference"></a>ATL 公用程式參考

ATL 提供程式碼操作的表單中的路徑與 Url [CPathT](../atl/reference/cpatht-class.md)並[CUrl](../atl/reference/curl-class.md)。 執行緒集區[CThreadPool](../atl/reference/cthreadpool-class.md)，可用於您的應用程式。 此程式碼可以找到 atlpath.h 和 atlutil.h 中。

### <a name="classes"></a>類別

|||
|-|-|
|[CPathT 類別](../atl/reference/cpatht-class.md)|此類別代表的路徑。|
|[CDebugReportHook 類別](../atl/reference/cdebugreporthook-class.md)|您可以使用這個類別，將偵錯報表傳送給具名管道。|
|[CNonStatelessWorker 類別](../atl/reference/cnonstatelessworker-class.md)|會從執行緒集區接收要求，並將其傳遞至會建立並終結背景工作物件中每個要求。|
|[CNoWorkerThread 類別](../atl/reference/cnoworkerthread-class.md)|使用這個類別做為引數`MonitorClass`樣板參數，如果您想要停用動態快取維護的快取類別。|
|[CThreadPool 類別](../atl/reference/cthreadpool-class.md)|這個類別會提供處理的工作項目佇列的背景工作執行緒集區。|
|[CUrl 類別](../atl/reference/curl-class.md)|這個類別表示的 URL。 它可讓您管理的獨立於其他 URL 的每個項目，是否剖析現有的 URL 字串，或從從頭開始建置字串。|
|[CWorkerThread 類別](../atl/reference/cworkerthread-class.md)|這個類別會建立背景工作執行緒或使用現有工作區、 等候一或多個核心物件控制代碼，而且其中一個控點而收到信號時，執行指定的用戶端函式。|

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
|[ATL_URL_SCHEME](../atl/reference/atl-url-scheme-enum.md)|這個列舉型別的成員提供了解配置常數[CUrl](../atl/reference/curl-class.md)。|

### <a name="functions"></a>函式

|||
|-|-|
|[AtlCanonicalizeUrl](../atl/reference/atl-http-utility-functions.md#atlcanonicalizeurl)|呼叫此函式可規範化 URL，包括將 Unsafe 字元和空格轉換成逸出序列。|
|[AtlCombineUrl](../atl/reference/atl-http-utility-functions.md#atlcombineurl)|呼叫此函式可將基底 URL 和相對 URL 結合成單一、標準的 URL。|
|[AtlEscapeUrl](../atl/reference/atl-http-utility-functions.md#atlescapeurl)|呼叫此函式會將所有 Unsafe 字元轉換成逸出序列。|
|[AtlGetDefaultUrlPort](../atl/reference/atl-http-utility-functions.md#atlgetdefaulturlport)|呼叫此函式可取得特定的網際網路通訊協定或配置相關聯的預設連接埠號碼。|
|[AtlHexValue](../atl/reference/atl-text-encoding-functions.md#atlhexvalue)|呼叫此函式可取得十六進位的數值。|
|[AtlIsUnsafeUrlChar](../atl/reference/atl-http-utility-functions.md#atlisunsafeurlchar)|呼叫此函式可了解在 URL 中使用某個字元是否安全。|
|[AtlUnescapeUrl](../atl/reference/atl-http-utility-functions.md#atlunescapeurl)|呼叫此函式將逸出字元轉換回其原始值。|
|[SystemTimeToHttpDate](../atl/reference/atl-http-utility-functions.md#systemtimetohttpdate)|呼叫此函式將系統時間轉換成採用適合在 HTTP 標頭中使用之格式的字串。|

|[ATLPath::AddBackslash](../atl/reference/atl-path-functions.md#addbackslash)|此函式是多載包裝函式[PathAddBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha
)。 | |[ATLPath::AddExtension](../atl/reference/atl-path-functions.md#addextension)|此函式是多載包裝函式[PathAddExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddextensiona)。 | |[ATLPath::Append](../atl/reference/atl-path-functions.md#append)|此函式是多載包裝函式[PathAppend](/windows/desktop/api/shlwapi/nf-shlwapi-pathappenda)。 | |[ATLPath::BuildRoot](../atl/reference/atl-path-functions.md#buildroot)|此函式是多載包裝函式[PathBuildRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathbuildroota)。 | |[ATLPath::Canonicalize](../atl/reference/atl-path-functions.md#canonicalize)|此函式是多載包裝函式[PathCanonicalize](/windows/desktop/api/shlwapi/nf-shlwapi-pathcanonicalizea)。 | |[ATLPath::Combine](../atl/reference/atl-path-functions.md#combine)|此函式是多載包裝函式[PathCombine](/windows/desktop/api/shlwapi/nf-shlwapi-pathcombinea)。 | |[ATLPath::CommonPrefix](../atl/reference/atl-path-functions.md#commonprefix)|此函式是多載包裝函式[PathCommonPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathcommonprefixa)。 | |[ATLPath::CompactPath](../atl/reference/atl-path-functions.md#compactpath)|此函式是多載包裝函式[PathCompactPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpatha)。 | |[ATLPath::CompactPathEx](../atl/reference/atl-path-functions.md#compactpathex)|此函式是多載包裝函式[PathCompactPathEx](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpathexa)。 | |[ATLPath::FileExists](../atl/reference/atl-path-functions.md#fileexists)|此函式是多載包裝函式[PathFileExists](/windows/desktop/api/shlwapi/nf-shlwapi-pathfileexistsa)。 | |[ATLPath::FindExtension](../atl/reference/atl-path-functions.md#findextension)|此函式是多載包裝函式[PathFindExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindextensiona)。 | |[ATLPath::FindFileName](../atl/reference/atl-path-functions.md#findfilename)|此函式是多載包裝函式[PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea)。 | |[ATLPath::GetDriveNumber](../atl/reference/atl-path-functions.md#getdrivenumber)|此函式是多載包裝函式[PathGetDriveNumber](/windows/desktop/api/shlwapi/nf-shlwapi-pathgetdrivenumbera)。 | |[ATLPath::IsDirectory](../atl/reference/atl-path-functions.md#isdirectory)|此函式是多載包裝函式[PathIsDirectory](/windows/desktop/api/shlwapi/nf-shlwapi-pathisdirectorya)。 | |[ATLPath::IsFileSpec](../atl/reference/atl-path-functions.md#isfilespec)|此函式是多載包裝函式[PathIsFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathisfilespeca)。 | |[ATLPath::IsPrefix](../atl/reference/atl-path-functions.md#isprefix)|此函式是多載包裝函式[PathIsPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathisprefixa)。 | |[ATLPath::IsRelative](../atl/reference/atl-path-functions.md#isrelative)|此函式是多載包裝函式[PathIsRelative](/windows/desktop/api/shlwapi/nf-shlwapi-pathisrelativea)。 | |[ATLPath::IsRoot](../atl/reference/atl-path-functions.md#isroot)|此函式是多載包裝函式[PathIsRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathisroota)。 | |[ATLPath::IsSameRoot](../atl/reference/atl-path-functions.md#issameroot)|此函式是多載包裝函式[PathIsSameRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathissameroota)。 | |[ATLPath::IsUNC](../atl/reference/atl-path-functions.md#isunc)|此函式是多載包裝函式[PathIsUNC](/windows/desktop/api/shlwapi/nf-shlwapi-pathisunca)。 | |[ATLPath::IsUNCServer](../atl/reference/atl-path-functions.md#isuncserver)|此函式是多載包裝函式[PathIsUNCServer](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncservera)。 | |[ATLPath::IsUNCServerShare](../atl/reference/atl-path-functions.md#isuncservershare)|此函式是多載包裝函式[PathIsUNCServerShare](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncserversharea).| |[ATLPath::MakePretty](../atl/reference/atl-path-functions.md#makepretty)|This function is an overloaded wrapper for [PathMakePretty](/windows/desktop/api/shlwapi/nf-shlwapi-pathmakeprettya).| |[ATLPath::MatchSpec](../atl/reference/atl-path-functions.md#matchspec)|This function is an overloaded wrapper for [PathMatchSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathmatchspeca).| |[ATLPath::QuoteSpaces](../atl/reference/atl-path-functions.md#quotespaces)|This function is an overloaded wrapper for [PathQuoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathquotespacesa).| |[ATLPath::RelativePathTo](../atl/reference/atl-path-functions.md#relativepathto)|This function is an overloaded wrapper for [PathRelativePathTo](/windows/desktop/api/shlwapi/nf-shlwapi-pathrelativepathtoa).| |[ATLPath::RemoveArgs](../atl/reference/atl-path-functions.md#removeargs)|This function is an overloaded wrapper for [PathRemoveArgs](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveargsa).| |[ATLPath::RemoveBackslash](../atl/reference/atl-path-functions.md#removebackslash)|This function is an overloaded wrapper for [PathRemoveBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovebackslasha).| |[ATLPath::RemoveBlanks](../atl/reference/atl-path-functions.md#removeblanks)|This function is an overloaded wrapper for [PathRemoveBlanks](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveblanksa).| |[ATLPath::RemoveExtension](../atl/reference/atl-path-functions.md#removeextension)|This function is an overloaded wrapper for [PathRemoveExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveextensiona).| |[ATLPath::RemoveFileSpec](../atl/reference/atl-path-functions.md#removefilespec)|This function is an overloaded wrapper for [PathRemoveFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovefilespeca).| |[ATLPath::RenameExtension](../atl/reference/atl-path-functions.md#renameextension)|This function is an overloaded wrapper for [PathRenameExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathrenameextensiona).| |[ATLPath::SkipRoot](../atl/reference/atl-path-functions.md#skiproot)|This function is an overloaded wrapper for [PathSkipRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathskiproota).| |[ATLPath::StripPath](../atl/reference/atl-path-functions.md#strippath)|This function is an overloaded wrapper for [PathStripPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathstrippatha).| |[ATLPath::StripToRoot](../atl/reference/atl-path-functions.md#striptoroot)|This function is an overloaded wrapper for [PathStripToRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathstriptoroota).| |[ATLPath::UnquoteSpaces](../atl/reference/atl-path-functions.md#unquotespaces)|This function is an overloaded wrapper for [PathUnquoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathunquotespacesa).|

## <a name="see-also"></a>另請參閱

[概念](../atl/active-template-library-atl-concepts.md)<br/>
[ATL COM 桌面元件](../atl/atl-com-desktop-components.md)
