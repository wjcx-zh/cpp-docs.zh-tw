---
title: ATL 公用程式參考
ms.date: 11/04/2016
ms.assetid: dd8a2888-34f4-461e-9bf4-834218f9b95b
ms.openlocfilehash: f9e59a2c67d391995d94d77f526613534acb48de
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831871"
---
# <a name="atl-utilities-reference"></a>ATL 公用程式參考

ATL 提供的程式碼會以 [CPathT](../atl/reference/cpatht-class.md) 和 [捲曲](../atl/reference/curl-class.md)的形式操作路徑和 url。 執行緒集區 [CThreadPool](../atl/reference/cthreadpool-class.md)可以在您的應用程式中使用。 此程式碼可以在 atlpath.h 和 atlutil.h 中找到。

## <a name="classes"></a>類別

| &nbsp; | &nbsp; |
|--|--|
| [CPathT 類別](../atl/reference/cpatht-class.md) | 此類別代表路徑。 |
| [CDebugReportHook 類別](../atl/reference/cdebugreporthook-class.md) | 使用這個類別可將 debug 報表傳送至具名管道。 |
| [CNonStatelessWorker 類別](../atl/reference/cnonstatelessworker-class.md) | 接收來自執行緒集區的要求，並將其傳遞至在每個要求上建立和終結的背景工作物件。 |
| [CNoWorkerThread 類別](../atl/reference/cnoworkerthread-class.md) | 如果您想要停用動態快取維護，請使用這個類別作為範本參數的引數，以快取 `MonitorClass` 類別。 |
| [CThreadPool 類別](../atl/reference/cthreadpool-class.md) | 這個類別會提供處理工作專案佇列的背景工作執行緒集區。 |
| [CUrl 類別](../atl/reference/curl-class.md) | 此類別代表 URL。 它可讓您管理 URL 的每個元素，而不是其他專案，無論是剖析現有的 URL 字串或從頭建立字串。 |
| [CWorkerThread 類別](../atl/reference/cworkerthread-class.md) | 這個類別會建立背景工作執行緒或使用現有的執行緒、等候一或多個核心物件控制碼，並在其中一個控制碼發出信號時執行指定的用戶端函數。 |

## <a name="typedefs"></a>Typedefs

| &emsp; | &emsp; |
|--|--|
| [CPath](../atl/reference/atl-typedefs.md#cpath) | 使用 [CPathT](../atl/reference/cpatht-class.md) 的特製化 `CString` 。 |
| [CPathA](../atl/reference/atl-typedefs.md#cpatha) | 使用 [CPathT](../atl/reference/cpatht-class.md) 的特製化 `CStringA` 。 |
| [CPathW](../atl/reference/atl-typedefs.md#cpathw) | 使用 [CPathT](../atl/reference/cpatht-class.md) 的特製化 `CStringW` 。 |
| [ATL_URL_PORT](../atl/reference/atl-typedefs.md#atl_url_port) | 由 [捲曲](../atl/reference/curl-class.md) 用來指定通訊埠編號的型別。 |

## <a name="enums"></a>列舉

| &emsp; | &emsp; |
|--|--|
| [ATL_URL_SCHEME](../atl/reference/atl-url-scheme-enum.md) | 此列舉的成員提供由 [捲曲](../atl/reference/curl-class.md)理解的配置常數。 |

## <a name="functions"></a>Functions

| &emsp; | &emsp; |
|--|--|
| [AtlCanonicalizeUrl](../atl/reference/atl-http-utility-functions.md#atlcanonicalizeurl) | 呼叫此函式可規範化 URL，包括將 Unsafe 字元和空格轉換成逸出序列。 |
| [AtlCombineUrl](../atl/reference/atl-http-utility-functions.md#atlcombineurl) | 呼叫此函式可將基底 URL 和相對 URL 結合成單一、標準的 URL。 |
| [AtlEscapeUrl](../atl/reference/atl-http-utility-functions.md#atlescapeurl) | 呼叫此函式會將所有 Unsafe 字元轉換成逸出序列。 |
| [AtlGetDefaultUrlPort](../atl/reference/atl-http-utility-functions.md#atlgetdefaulturlport) | 呼叫此函式可取得與特定網際網路通訊協定或配置相關聯的預設通訊埠編號。 |
| [AtlHexValue](../atl/reference/atl-text-encoding-functions.md#atlhexvalue) | 呼叫此函式可取得十六進位的數值。 |
| [AtlIsUnsafeUrlChar](../atl/reference/atl-http-utility-functions.md#atlisunsafeurlchar) | 呼叫此函式可了解在 URL 中使用某個字元是否安全。 |
| [AtlUnescapeUrl](../atl/reference/atl-http-utility-functions.md#atlunescapeurl) | 呼叫此函式將逸出字元轉換回其原始值。 |
| [SystemTimeToHttpDate](../atl/reference/atl-http-utility-functions.md#systemtimetohttpdate) | 呼叫此函式將系統時間轉換成採用適合在 HTTP 標頭中使用之格式的字串。 |
| [ATLPath::AddBackslash](../atl/reference/atl-path-functions.md#addbackslash) | 此函數是 [Pathaddbackslash 式] (/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha 的多載包裝函式 |
| ). |
| [ATLPath::AddExtension](../atl/reference/atl-path-functions.md#addextension) | 此函數是 [pathaddextension 式](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw)的多載包裝函式。 |
| [ATLPath::Append](../atl/reference/atl-path-functions.md#append) | 此函數是 [pathappend 式](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw)的多載包裝函式。 |
| [ATLPath::BuildRoot](../atl/reference/atl-path-functions.md#buildroot) | 此函數是 [pathbuildroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw)的多載包裝函式。 |
| [ATLPath::Canonicalize](../atl/reference/atl-path-functions.md#canonicalize) | 此函數是 [pathcanonicalize 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew)的多載包裝函式。 |
| [ATLPath::Combine](../atl/reference/atl-path-functions.md#combine) | 此函數是 [pathcombine 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew)的多載包裝函式。 |
| [ATLPath::CommonPrefix](../atl/reference/atl-path-functions.md#commonprefix) | 此函數是 [pathcommonprefix 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw)的多載包裝函式。 |
| [ATLPath::CompactPath](../atl/reference/atl-path-functions.md#compactpath) | 此函數是 [pathcompactpath 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw)的多載包裝函式。 |
| [ATLPath::CompactPathEx](../atl/reference/atl-path-functions.md#compactpathex) | 此函數是 [pathcompactpathex 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw)的多載包裝函式。 |
| [ATLPath::FileExists](../atl/reference/atl-path-functions.md#fileexists) | 此函數是 [pathfileexists 式](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw)的多載包裝函式。 |
| [ATLPath::FindExtension](../atl/reference/atl-path-functions.md#findextension) | 此函數是 [pathfindextension 式](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw)的多載包裝函式。 |
| [ATLPath::FindFileName](../atl/reference/atl-path-functions.md#findfilename) | 此函數是 [pathfindfilename 式](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)的多載包裝函式。 |
| [ATLPath::GetDriveNumber](../atl/reference/atl-path-functions.md#getdrivenumber) | 此函數是 [pathgetdrivenumber 式](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw)的多載包裝函式。 |
| [ATLPath::IsDirectory](../atl/reference/atl-path-functions.md#isdirectory) | 此函數是 [pathisdirectory 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw)的多載包裝函式。 |
| [ATLPath::IsFileSpec](../atl/reference/atl-path-functions.md#isfilespec) | 此函數是 [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw)的多載包裝函式。 |
| [ATLPath::IsPrefix](../atl/reference/atl-path-functions.md#isprefix) | 此函數是 [pathisprefix 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)的多載包裝函式。 |
| [ATLPath::IsRelative](../atl/reference/atl-path-functions.md#isrelative) | 此函數是 [pathisrelative 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew)的多載包裝函式。 |
| [ATLPath::IsRoot](../atl/reference/atl-path-functions.md#isroot) | 此函數是 [pathisroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw)的多載包裝函式。 |
| [ATLPath::IsSameRoot](../atl/reference/atl-path-functions.md#issameroot) | 此函數是 [pathissameroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw)的多載包裝函式。 |
| [ATLPath::IsUNC](../atl/reference/atl-path-functions.md#isunc) | 此函數是 [pathisunc 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw)的多載包裝函式。 |
| [ATLPath::IsUNCServer](../atl/reference/atl-path-functions.md#isuncserver) | 此函數是 [pathisuncserver 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw)的多載包裝函式。 |
| [ATLPath::IsUNCServerShare](../atl/reference/atl-path-functions.md#isuncservershare) | 此函數是 [pathisuncservershare 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew)的多載包裝函式。 |
| [ATLPath::MakePretty](../atl/reference/atl-path-functions.md#makepretty) | 此函數是 [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw)的多載包裝函式。 |
| [ATLPath::MatchSpec](../atl/reference/atl-path-functions.md#matchspec) | 此函數是 [pathmatchspec 式](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw)的多載包裝函式。 |
| [ATLPath::QuoteSpaces](../atl/reference/atl-path-functions.md#quotespaces) | 此函數是 [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw)的多載包裝函式。 |
| [ATLPath::RelativePathTo](../atl/reference/atl-path-functions.md#relativepathto) | 此函數是 [pathrelativepathto 式](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow)的多載包裝函式。 |
| [ATLPath::RemoveArgs](../atl/reference/atl-path-functions.md#removeargs) | 此函數是 [pathremoveargs 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw)的多載包裝函式。 |
| [ATLPath::RemoveBackslash](../atl/reference/atl-path-functions.md#removebackslash) | 此函數是 [pathremovebackslash 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw)的多載包裝函式。 |
| [ATLPath::RemoveBlanks](../atl/reference/atl-path-functions.md#removeblanks) | 此函數是 [pathremoveblanks 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw)的多載包裝函式。 |
| [ATLPath::RemoveExtension](../atl/reference/atl-path-functions.md#removeextension) | 此函數是 [pathremoveextension 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw)的多載包裝函式。 |
| [ATLPath::RemoveFileSpec](../atl/reference/atl-path-functions.md#removefilespec) | 此函數是 [pathremovefilespec 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw)的多載包裝函式。 |
| [ATLPath::RenameExtension](../atl/reference/atl-path-functions.md#renameextension) | 此函數是 [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw)的多載包裝函式。 |
| [ATLPath::SkipRoot](../atl/reference/atl-path-functions.md#skiproot) | 此函數是 [pathskiproot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw)的多載包裝函式。 |
| [ATLPath::StripPath](../atl/reference/atl-path-functions.md#strippath) | 此函數是 [pathstrippath 式](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw)的多載包裝函式。 |
| [ATLPath::StripToRoot](../atl/reference/atl-path-functions.md#striptoroot) | 此函數是 [pathstriptoroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw)的多載包裝函式。 |
| [ATLPath::UnquoteSpaces](../atl/reference/atl-path-functions.md#unquotespaces) | 此函數是 [pathunquotespaces 式](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw)的多載包裝函式。 |

## <a name="see-also"></a>另請參閱

[概念](../atl/active-template-library-atl-concepts.md)<br/>
[ATL COM 桌面元件](../atl/atl-com-desktop-components.md)
