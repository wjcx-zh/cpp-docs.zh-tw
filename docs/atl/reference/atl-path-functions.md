---
title: ATL 路徑函數
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, path
f1_keywords:
- ATLPATH/ATL::ATLPath::AddBackslash
- ATLPATH/ATL::ATLPath::AddExtension
- ATLPATH/ATL::ATLPath::Append
- ATLPATH/ATL::ATLPath::BuildRoot
- ATLPATH/ATL::ATLPath::Canonicalize
- ATLPATH/ATL::ATLPath::Combine
- ATLPATH/ATL::ATLPath::CommonPrefix
- ATLPATH/ATL::ATLPath::CompactPath
- ATLPATH/ATL::ATLPath::CompactPathEx
- ATLPATH/ATL::ATLPath::FileExists
- ATLPATH/ATL::ATLPath::FindExtension
- ATLPATH/ATL::ATLPath::FindFileName
- ATLPATH/ATL::ATLPath::GetDriveNumber
- ATLPATH/ATL::ATLPath::IsDirectory
- ATLPATH/ATL::ATLPath::IsFileSpec
- ATLPATH/ATL::ATLPath::IsPrefix
- ATLPATH/ATL::ATLPath::IsRelative
- ATLPATH/ATL::ATLPath::IsRoot
- ATLPATH/ATL::ATLPath::IsSameRoot
- ATLPATH/ATL::ATLPath::IsUNC
- ATLPATH/ATL::ATLPath::IsUNCServer
- ATLPATH/ATL::ATLPath::IsUNCServerShare
- ATLPATH/ATL::ATLPath::MakePretty
- ATLPATH/ATL::ATLPath::MatchSpec
- ATLPATH/ATL::ATLPath::QuoteSpaces
- ATLPATH/ATL::ATLPath::RelativePathTo
- ATLPATH/ATL::ATLPath::RemoveArgs
- ATLPATH/ATL::ATLPath::RemoveBackslash
- ATLPATH/ATL::ATLPath::RemoveBlanks
- ATLPATH/ATL::ATLPath::RemoveExtension
- ATLPATH/ATL::ATLPath::RemoveFileSpec
- ATLPATH/ATL::ATLPath::RenameExtension
- ATLPATH/ATL::ATLPath::SkipRoot
- ATLPATH/ATL::ATLPath::StripPath
- ATLPATH/ATL::ATLPath::StripToRoot
- ATLPATH/ATL::ATLPath::UnquoteSpaces
ms.assetid: d1ec2b8d-7ec7-43ea-90dd-0a740d2a742b
ms.openlocfilehash: f3d8fa63e7fd20f8a0d6759fee8417b3fbc29486
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319212"
---
# <a name="atl-path-functions"></a>ATL 路徑函數

ATL 提供 ATLPath 類,用於以[CPathT](cpatht-class.md)的形式操作路徑。 此代碼可在 atlpath.h 中找到。

### <a name="related-classes"></a>相關類

|||
|-|-|
|[CPathT 類別](cpatht-class.md)|此類表示路徑。|

### <a name="related-typedefs"></a>相關類型

|||
|-|-|
|`CPath`|使用[的 CPathT](cpatht-class.md)的專門`CString`化。|
|`CPathA`|使用[的 CPathT](cpatht-class.md)的專門`CStringA`化。|
|`CPathW`|使用[的 CPathT](cpatht-class.md)的專門`CStringW`化。|

### <a name="functions"></a>函式

|||
|-|-|
|[ATLPath::AddBackslash](#addbackslash)|此函數是[PathAddBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw)的重載包裝。|
|[ATLPath::AddExtension](#addextension)|此函數是[PathAdd 擴展](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw)的重載包裝器。|
|[ATLPath::Append](#append)|此函數是[PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw)的重載包裝器。|
|[ATLPath::BuildRoot](#buildroot)|此函數是[PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw)的重載包裝器。|
|[ATLPath::Canonicalize](#canonicalize)|此函數是[PathCanicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew)的重載包裝。|
|[ATLPath::Combine](#combine)|此函數是[PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew)的重載包裝器。|
|[ATLPath::CommonPrefix](#commonprefix)|此函數是[PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw)的重載包裝器。|
|[ATLPath::CompactPath](#compactpath)|此函數是[PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw)的重載包裝器。|
|[ATLPath::CompactPathEx](#compactpathex)|此函數是[PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw)的重載包裝器。|
|[ATLPath::FileExists](#fileexists)|此函數是[PathFile 存在](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw)的重載包裝器。|
|[ATLPath::FindExtension](#findextension)|此函數是[PathFind 擴展](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw)的重載包裝器。|
|[ATLPath::FindFileName](#findfilename)|此函數是[PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)的重載包裝。|
|[ATLPath::GetDriveNumber](#getdrivenumber)|此函數是[PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw)的重載包裝。|
|[ATLPath::IsDirectory](#isdirectory)|此函數是[PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw)的重載包裝器。|
|[ATLPath::IsFileSpec](#isfilespec)|此函數是[PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw)的重載包裝。|
|[ATLPath::IsPrefix](#isprefix)|此函數是[PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)的重載包裝器。|
|[ATLPath::IsRelative](#isrelative)|此函數是[PathIs 相對](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew)的重載包裝器。|
|[ATLPath::IsRoot](#isroot)|此函數是[PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw)的重載包裝器。|
|[ATLPath::IsSameRoot](#issameroot)|此函數是[PathIs SameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw)的重載包裝。|
|[ATLPath::IsUNC](#isunc)|此函數是[PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw)的重載包裝器。|
|[ATLPath::IsUNCServer](#isuncserver)|此函數是[PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw)的重載包裝器。|
|[ATLPath::IsUNCServerShare](#isuncservershare)|此函數是[PathIsUNCServer 的](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew)重載包裝。|
|[ATLPath::MakePretty](#makepretty)|此函數是[PathMakePretty 的](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw)重載包裝器。|
|[ATLPath::MatchSpec](#matchspec)|此函數是[PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw)的重載包裝器。|
|[ATLPath::QuoteSpaces](#quotespaces)|此函數是[PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw)的重載包裝器。|
|[ATLPath::RelativePathTo](#relativepathto)|此函數是[Path相對路徑的](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow)重載包裝。|
|[ATLPath::RemoveArgs](#removeargs)|此函數是[PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw)的重載包裝器。|
|[ATLPath::RemoveBackslash](#removebackslash)|此函數是[路徑刪除反斜杠](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw)的重載包裝。|
|[ATLPath::RemoveBlanks](#removeblanks)|此函數是[PathRemoveBlank 的](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw)重載包裝。|
|[ATLPath::RemoveExtension](#removeextension)|此函數是[路徑刪除擴展](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw)的重載包裝器。|
|[ATLPath::RemoveFileSpec](#removefilespec)|此函數是[PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw)的重載包裝器。|
|[ATLPath::RenameExtension](#renameextension)|此函數是[路徑重新命名擴展](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw)的重載包裝器。|
|[ATLPath::SkipRoot](#skiproot)|此函數是[PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw)的重載包裝器。|
|[ATLPath::StripPath](#strippath)|此函數是[PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw)的重載包裝器。|
|[ATLPath::StripToRoot](#striptoroot)|此函數是[PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw)的重載包裝器。|
|[ATLPath::UnquoteSpaces](#unquotespaces)|此函數是[PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw)的重載包裝。|

## <a name="requirements"></a>需求

**標題:** atlpath.h

## <a name="atlpathaddbackslash"></a><a name="addbackslash"></a>ATLPath::添加回斜杠

此函數是[PathAddBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw)的重載包裝。

### <a name="syntax"></a>語法

```
inline char* AddBackslash(char* pszPath);
inline wchar_t* AddBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[路徑新增反斜槓](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw)。

## <a name="atlpathaddextension"></a><a name="addextension"></a>ATLPath:新增擴展

此函數是[PathAdd 擴展](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw)的重載包裝器。

### <a name="syntax"></a>語法

```
inline BOOL AddExtension(char* pszPath, const char* pszExtension);
inline BOOL AddExtension(wchar_t* pszPath, const wchar_t* pszExtension);
```

### <a name="remarks"></a>備註

有關詳細資訊,請參考[路徑新增擴充](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw)。

## <a name="atlpathappend"></a><a name="append"></a>ATLPath:附加

此函數是[PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw)的重載包裝器。

### <a name="syntax"></a>語法

```
inline BOOL Append(char* pszPath, const char* pszMore);
inline BOOL Append(wchar_t* pszPath, const wchar_t* pszMore);
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[路徑應用](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw)。

## <a name="atlpathbuildroot"></a><a name="buildroot"></a>ATLPath::建構根

此函數是[PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw)的重載包裝器。

### <a name="syntax"></a>語法

```
inline char* BuildRoot(char* pszPath, int iDrive);
inline wchar_t* BuildRoot(wchar_t* pszPath, int iDrive);
```

### <a name="remarks"></a>備註

有關詳細資訊[,請參考路徑編譯根](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw)。

## <a name="atlpathcanonicalize"></a><a name="canonicalize"></a>ATLPath:規範

此函數是[PathCanicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew)的重載包裝。

### <a name="syntax"></a>語法

```
inline BOOL Canonicalize(char* pszDest, const char* pszSrc);
inline BOOL Canonicalize(wchar_t* pszDest, const wchar_t* pszSrc);
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[路徑規範](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew)。

## <a name="atlpathcombine"></a><a name="combine"></a>ATLPath:合併

此函數是[PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew)的重載包裝器。

### <a name="syntax"></a>語法

```
inline char* Combine(
   char* pszDest,
   const char* pszDir,
   const char* pszFile
);

inline wchar_t* Combine(
   wchar_t* pszDest,
   const wchar_t* pszDir,
   const wchar_t* pszFile);
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱路徑組合。

## <a name="atlpathcommonprefix"></a><a name="commonprefix"></a>ATLPath::通用首頭

此函數是[PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw)的重載包裝器。

### <a name="syntax"></a>語法

```
inline int CommonPrefix(
   const char* pszFile1,
   const char* pszFile2,
   char* pszDest);

inline int CommonPrefix(
   const wchar_t* pszFile1,
   const wchar_t* pszFile2,
   wchar_t* pszDest);
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[路徑公共前置字](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw)串 。

## <a name="atlpathcompactpath"></a><a name="compactpath"></a>ATLPath:壓縮路徑

此函數是[PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw)的重載包裝器。

### <a name="syntax"></a>語法

```
inline BOOL CompactPath(
   HDC hDC,
   char* pszPath,
   UINT dx);

inline BOOL CompactPath(
   HDC hDC,
   wchar_t* pszPath,
   UINT dx);
```

### <a name="remarks"></a>備註

有關詳細資訊,請參考[路徑壓縮路徑](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw)。

## <a name="atlpathcompactpathex"></a><a name="compactpathex"></a>ATLPath::緊湊型路徑

此函數是[PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw)的重載包裝器。

### <a name="syntax"></a>語法

```
inline BOOL CompactPathEx(
   char* pszDest,
   const char* pszSrc,
   UINT nMaxChars,
   DWORD dwFlags);

inline BOOL CompactPathEx(
   wchar_t* pszDest,
   const wchar_t* pszSrc,
   UINT nMaxChars,
   DWORD dwFlags);
```

### <a name="remarks"></a>備註

有關詳細資訊[,請參閱路徑壓縮路徑Ex。](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw)

## <a name="atlpathfileexists"></a><a name="fileexists"></a>ATLPath:檔案存在

此函數是[PathFile 存在](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw)的重載包裝器。

### <a name="syntax"></a>語法

```
inline BOOL FileExists(const char* pszPath);
inline BOOL FileExists(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

有關詳細資訊[,請參閱 PathFile 存在](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw)。

## <a name="atlpathfindextension"></a><a name="findextension"></a>ATLPath::尋找擴充

此函數是[PathFind 擴展](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw)的重載包裝器。

### <a name="syntax"></a>語法

```
inline char* FindExtension(const char* pszPath);
inline wchar_t* FindExtension(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

有關詳細資訊[,請參考路徑尋找擴充](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw)。

## <a name="atlpathfindfilename"></a><a name="findfilename"></a>ATLPath:尋找檔案名稱

此函數是[PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)的重載包裝。

### <a name="syntax"></a>語法

```
inline char* FindFileName(const char* pszPath);
inline wchar_t* FindFileName(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

關於詳細資訊[,請參考路徑尋找檔案名稱](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)。

## <a name="atlpathgetdrivenumber"></a><a name="getdrivenumber"></a>ATLPath:取得磁碟機號碼

此函數是[PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw)的重載包裝。

### <a name="syntax"></a>語法

```
inline int GetDriveNumber(const char* pszPath);
inline int GetDriveNumber(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

有關詳細資訊[,請參閱 PathGetDrive 編號](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw)。

## <a name="atlpathisdirectory"></a><a name="isdirectory"></a>ATLPath:是目錄

此函數是[PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw)的重載包裝器。

```
inline BOOL IsDirectory(const char* pszPath);
inline BOOL IsDirectory(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱 PathIsDirectory。

## <a name="atlpathisfilespec"></a><a name="isfilespec"></a>ATLPath:是檔案規格

此函數是[PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw)的重載包裝。

### <a name="syntax"></a>語法

```
inline BOOL IsFileSpec(const char* pszPath);
inline BOOL IsFileSpec(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

有關詳細資訊[,請參閱 PathIsFileSpec。](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw)

## <a name="atlpathisprefix"></a><a name="isprefix"></a>ATLPath:isprefix

此函數是[PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)的重載包裝器。

### <a name="syntax"></a>語法

```
inline BOOL IsPrefix(const char* pszPrefix, const char* pszPath);
inline BOOL IsPrefix(const wchar_t* pszPrefix, const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

有關詳細資訊[,請參閱 PathIsPrefix。](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)

## <a name="atlpathisrelative"></a><a name="isrelative"></a>ATLPath:相對

此函數是[PathIs 相對](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew)的重載包裝器。

### <a name="syntax"></a>語法

```
inline BOOL IsRelative(const char* pszPath);
inline BOOL IsRelative(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[路徑相關](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew)。

## <a name="atlpathisroot"></a><a name="isroot"></a>ATLPath:是根

此函數是[PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw)的重載包裝器。

### <a name="syntax"></a>語法

```
inline BOOL IsRoot(const char* pszPath);
inline BOOL IsRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

有關詳細資訊[,請參閱 PathIsRoot。](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw)

## <a name="atlpathissameroot"></a><a name="issameroot"></a>ATLPath::是同根

此函數是[PathIs SameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw)的重載包裝。

### <a name="syntax"></a>語法

```
inline BOOL IsSameRoot(const char* pszPath1, const char* pszPath2);
inline BOOL IsSameRoot(const wchar_t* pszPath1, const wchar_t* pszPath2);
```

### <a name="remarks"></a>備註

有關詳細資訊[,請參閱路徑 IsSameRoot。](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw)

## <a name="atlpathisunc"></a><a name="isunc"></a>ATLPath:IsUNC

此函數是[PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw)的重載包裝器。

### <a name="syntax"></a>語法

```
inline BOOL IsUNC(const char* pszPath);
inline BOOL IsUNC(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

有關詳細資訊[,請參閱 PathIsUNC。](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw)

## <a name="atlpathisuncserver"></a><a name="isuncserver"></a>ATLPath:isUNCServer

此函數是[PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw)的重載包裝器。

### <a name="syntax"></a>語法

```
inline BOOL IsUNCServer(const char* pszPath);
inline BOOL IsUNCServer(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

有關詳細資訊[,請參閱 PathIsUNCServer。](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw)

## <a name="atlpathisuncservershare"></a><a name="isuncservershare"></a>ATLPath:isUNCServer共用

此函數是[PathIsUNCServer 的](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew)重載包裝。

### <a name="syntax"></a>語法

```
inline BOOL IsUNCServerShare(const char* pszPath);
inline BOOL IsUNCServerShare(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

有關詳細資訊[,請參閱 PathIsUNCServer 共用](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew)。

## <a name="atlpathmakepretty"></a><a name="makepretty"></a>ATLPath:讓漂亮

此函數是[PathMakePretty 的](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw)重載包裝器。

### <a name="syntax"></a>語法

```
inline BOOL MakePretty(char* pszPath);
inline BOOL MakePretty(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[PathMake"美麗](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw)"。

## <a name="atlpathmatchspec"></a><a name="matchspec"></a>ATLPath::匹配規格

此函數是[PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw)的重載包裝器。

### <a name="syntax"></a>語法

```
inline BOOL MatchSpec(const char* pszPath, const char* pszSpec);
inline BOOL MatchSpec(const wchar_t* pszPath, const wchar_t* pszSpec);
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[路徑匹配Spec。](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw)

## <a name="atlpathquotespaces"></a><a name="quotespaces"></a>ATLPath::報價空間

此函數是[PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw)的重載包裝器。

### <a name="syntax"></a>語法

```
inline void QuoteSpaces(char* pszPath);
inline void QuoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[路徑報價空間](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw)。

## <a name="atlpathrelativepathto"></a><a name="relativepathto"></a>ATLPath:相對路徑

此函數是[Path相對路徑的](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow)重載包裝。

### <a name="syntax"></a>語法

```
inline BOOL RelativePathTo(
   char* pszPath,
   const char* pszFrom,
   DWORD dwAttrFrom,
   const char* pszTo,
   DWORD dwAttrTo);

inline BOOL RelativePathTo(
   wchar_t* pszPath,
   const wchar_t* pszFrom,
   DWORD dwAttrFrom,
   const wchar_t* pszTo,
   DWORD dwAttrTo);
```

### <a name="remarks"></a>備註

有關詳細資訊[,請參閱路徑相關路徑。](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow)

## <a name="atlpathremoveargs"></a><a name="removeargs"></a>ATLPath::刪除阿格

此函數是[PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw)的重載包裝器。

### <a name="syntax"></a>語法

```
inline void RemoveArgs(char* pszPath);
inline void RemoveArgs(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[路徑刪除。](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw)

## <a name="atlpathremovebackslash"></a><a name="removebackslash"></a>ATLPath::刪除反斜杠

此函數是[路徑刪除反斜杠](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw)的重載包裝。

### <a name="syntax"></a>語法

```
inline char* RemoveBackslash(char* pszPath);
inline wchar_t* RemoveBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

關於詳細資訊[,請參考路徑刪除反斜槓](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw)。

## <a name="atlpathremoveblanks"></a><a name="removeblanks"></a>ATLPath::刪除空白

此函數是[PathRemoveBlank 的](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw)重載包裝。

### <a name="syntax"></a>語法

```
inline void RemoveBlanks(char* pszPath);
inline void RemoveBlanks(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

有關詳細資訊,請參考[空白](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw)。

## <a name="atlpathremoveextension"></a><a name="removeextension"></a>ATLPath::刪除擴展

此函數是[路徑刪除擴展](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw)的重載包裝器。

### <a name="syntax"></a>語法

```
inline void RemoveExtension(char* pszPath);
inline void RemoveExtension(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

關於詳細資訊[,請參考此資料夾刪除延伸](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw)。

## <a name="atlpathremovefilespec"></a><a name="removefilespec"></a>ATLPath::刪除檔案規格

此函數是[PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw)的重載包裝器。

### <a name="syntax"></a>語法

```
inline BOOL RemoveFileSpec(char* pszPath);
inline BOOL RemoveFileSpec(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

有關詳細資訊[,請參閱路徑刪除檔Spec。](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw)

## <a name="atlpathrenameextension"></a><a name="renameextension"></a>ATLPath:重新命名擴充

此函數是[路徑重新命名擴展](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw)的重載包裝器。

### <a name="syntax"></a>語法

```
inline BOOL RenameExtension(char* pszPath, const char* pszExt);
inline BOOL RenameExtension(wchar_t* pszPath, const wchar_t* pszExt);
```

### <a name="remarks"></a>備註

有關詳細資訊,請參考[路徑重新命名延伸](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw)。

## <a name="atlpathskiproot"></a><a name="skiproot"></a>ATLPath::跳過根

此函數是[PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw)的重載包裝器。

### <a name="syntax"></a>語法

```
inline char* SkipRoot(const char* pszPath);
inline wchar_t* SkipRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[路徑跳過根](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw)。

## <a name="atlpathstrippath"></a><a name="strippath"></a>ATLPath:條帶路徑

此函數是[PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw)的重載包裝器。

### <a name="syntax"></a>語法

```
inline void StripPath(char* pszPath);
inline void StripPath(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[路徑條帶路徑](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw)。

## <a name="atlpathstriptoroot"></a><a name="striptoroot"></a>ATLPath::條紋根

此函數是[PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw)的重載包裝器。

### <a name="syntax"></a>語法

```
inline BOOL StripToRoot(char* pszPath);
inline BOOL StripToRoot(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[路徑條帶。](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw)

## <a name="atlpathunquotespaces"></a><a name="unquotespaces"></a>ATLPath::無引號空格

此函數是[PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw)的重載包裝。

### <a name="syntax"></a>語法

```
inline void UnquoteSpaces(char* pszPath);
inline void UnquoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[路徑取消引號空間](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw)。
