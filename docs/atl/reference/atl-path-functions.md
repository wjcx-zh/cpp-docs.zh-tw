---
title: ATL 路徑函式
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
ms.openlocfilehash: 86ddb3c6916675a92070684a04c7a6a6ecd8a134
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586065"
---
# <a name="atl-path-functions"></a>ATL 路徑函式

ATL 提供 ATLPath 類別，以管理路徑的形式[CPathT](cpatht-class.md)。 此程式碼可以找到 atlpath.h 中。

### <a name="related-classes"></a>相關的類別

|||
|-|-|
|[CPathT 類別](cpatht-class.md)|此類別代表的路徑。|

### <a name="related-typedefs"></a>相關的 Typedef

|||
|-|-|
|`CPath`|特製化[CPathT](cpatht-class.md)使用`CString`。|
|`CPathA`|特製化[CPathT](cpatht-class.md)使用`CStringA`。|
|`CPathW`|特製化[CPathT](cpatht-class.md)使用`CStringW`。|

### <a name="functions"></a>函式

|||
|-|-|
|[ATLPath::AddBackslash](#addbackslash)|此函式是多載包裝函式[PathAddBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha)。|
|[ATLPath::AddExtension](#addextension)|此函式是多載包裝函式[PathAddExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddextensiona)。|
|[ATLPath::Append](#append)|此函式是多載包裝函式[PathAppend](/windows/desktop/api/shlwapi/nf-shlwapi-pathappenda)。|
|[ATLPath::BuildRoot](#buildroot)|此函式是多載包裝函式[PathBuildRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathbuildroota)。|
|[ATLPath::Canonicalize](#canonicalize)|此函式是多載包裝函式[PathCanonicalize](/windows/desktop/api/shlwapi/nf-shlwapi-pathcanonicalizea)。|
|[ATLPath::Combine](#combine)|此函式是多載包裝函式[PathCombine](/windows/desktop/api/shlwapi/nf-shlwapi-pathcombinea)。|
|[ATLPath::CommonPrefix](#commonprefix)|此函式是多載包裝函式[PathCommonPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathcommonprefixa)。|
|[ATLPath::CompactPath](#compactpath)|此函式是多載包裝函式[PathCompactPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpatha)。|
|[ATLPath::CompactPathEx](#compactpathex)|此函式是多載包裝函式[PathCompactPathEx](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpathexa)。|
|[ATLPath::FileExists](#fileexists)|此函式是多載包裝函式[PathFileExists](/windows/desktop/api/shlwapi/nf-shlwapi-pathfileexistsa)。|
|[ATLPath::FindExtension](#findextension)|此函式是多載包裝函式[PathFindExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindextensiona)。|
|[ATLPath::FindFileName](#findfilename)|此函式是多載包裝函式[PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea)。|
|[ATLPath::GetDriveNumber](#getdrivenumber)|此函式是多載包裝函式[PathGetDriveNumber](/windows/desktop/api/shlwapi/nf-shlwapi-pathgetdrivenumbera)。|
|[ATLPath::IsDirectory](#isdirectory)|此函式是多載包裝函式[PathIsDirectory](/windows/desktop/api/shlwapi/nf-shlwapi-pathisdirectorya)。|
|[ATLPath::IsFileSpec](#isfilespec)|此函式是多載包裝函式[PathIsFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathisfilespeca)。|
|[ATLPath::IsPrefix](#isprefix)|此函式是多載包裝函式[PathIsPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathisprefixa)。|
|[ATLPath::IsRelative](#isrelative)|此函式是多載包裝函式[PathIsRelative](/windows/desktop/api/shlwapi/nf-shlwapi-pathisrelativea)。|
|[ATLPath::IsRoot](#isroot)|此函式是多載包裝函式[PathIsRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathisroota)。|
|[ATLPath::IsSameRoot](#issameroot)|此函式是多載包裝函式[PathIsSameRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathissameroota)。|
|[ATLPath::IsUNC](#isunc)|此函式是多載包裝函式[PathIsUNC](/windows/desktop/api/shlwapi/nf-shlwapi-pathisunca)。|
|[ATLPath::IsUNCServer](#isuncserver)|此函式是多載包裝函式[PathIsUNCServer](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncservera)。|
|[ATLPath::IsUNCServerShare](#isuncservershare)|此函式是多載包裝函式[PathIsUNCServerShare](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncserversharea)。|
|[ATLPath::MakePretty](#makepretty)|此函式是多載包裝函式[PathMakePretty](/windows/desktop/api/shlwapi/nf-shlwapi-pathmakeprettya)。|
|[ATLPath::MatchSpec](#matchspec)|此函式是多載包裝函式[PathMatchSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathmatchspeca)。|
|[ATLPath::QuoteSpaces](#quotespaces)|此函式是多載包裝函式[PathQuoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathquotespacesa)。|
|[ATLPath::RelativePathTo](#relativepathto)|此函式是多載包裝函式[PathRelativePathTo](/windows/desktop/api/shlwapi/nf-shlwapi-pathrelativepathtoa)。|
|[ATLPath::RemoveArgs](#removeargs)|此函式是多載包裝函式[PathRemoveArgs](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveargsa)。|
|[ATLPath::RemoveBackslash](#removebackslash)|此函式是多載包裝函式[PathRemoveBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovebackslasha)。|
|[ATLPath::RemoveBlanks](#removeblanks)|此函式是多載包裝函式[PathRemoveBlanks](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveblanksa)。|
|[ATLPath::RemoveExtension](#removeextension)|此函式是多載包裝函式[PathRemoveExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveextensiona)。|
|[ATLPath::RemoveFileSpec](#removefilespec)|此函式是多載包裝函式[PathRemoveFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovefilespeca)。|
|[ATLPath::RenameExtension](#renameextension)|此函式是多載包裝函式[PathRenameExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathrenameextensiona)。|
|[ATLPath::SkipRoot](#skiproot)|此函式是多載包裝函式[PathSkipRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathskiproota)。|
|[ATLPath::StripPath](#strippath)|此函式是多載包裝函式[PathStripPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathstrippatha)。|
|[ATLPath::StripToRoot](#striptoroot)|此函式是多載包裝函式[PathStripToRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathstriptoroota)。|
|[ATLPath::UnquoteSpaces](#unquotespaces)|此函式是多載包裝函式[PathUnquoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathunquotespacesa)。|

## <a name="requirements"></a>需求

**標頭：** atlpath.h

## <a name="addbackslash"></a> ATLPath::AddBackSlash

此函式是多載包裝函式[PathAddBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha)。

### <a name="syntax"></a>語法

```
inline char* AddBackslash(char* pszPath);
inline wchar_t* AddBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

請參閱[PathAddBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha)如需詳細資訊。

## <a name="addextension"></a> ATLPath::AddExtension

此函式是多載包裝函式[PathAddExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddextensiona)。

### <a name="syntax"></a>語法

```
inline BOOL AddExtension(char* pszPath, const char* pszExtension);
inline BOOL AddExtension(wchar_t* pszPath, const wchar_t* pszExtension);
```

### <a name="remarks"></a>備註

請參閱[PathAddExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddextensiona)如需詳細資訊。

## <a name="append"></a> ATLPath::Append

此函式是多載包裝函式[PathAppend](/windows/desktop/api/shlwapi/nf-shlwapi-pathappenda)。

### <a name="syntax"></a>語法

```
inline BOOL Append(char* pszPath, const char* pszMore);
inline BOOL Append(wchar_t* pszPath, const wchar_t* pszMore);
```

### <a name="remarks"></a>備註

請參閱[PathAppend](/windows/desktop/api/shlwapi/nf-shlwapi-pathappenda)如需詳細資訊。

## <a name="buildroot"></a> ATLPath::BuildRoot

此函式是多載包裝函式[PathBuildRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathbuildroota)。

### <a name="syntax"></a>語法

```
inline char* BuildRoot(char* pszPath, int iDrive);
inline wchar_t* BuildRoot(wchar_t* pszPath, int iDrive);
```

### <a name="remarks"></a>備註

請參閱[PathBuildRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathbuildroota)如需詳細資訊。

## <a name="canonicalize"></a> ATLPath::Canonicalize

此函式是多載包裝函式[PathCanonicalize](/windows/desktop/api/shlwapi/nf-shlwapi-pathcanonicalizea)。

### <a name="syntax"></a>語法

```
inline BOOL Canonicalize(char* pszDest, const char* pszSrc);
inline BOOL Canonicalize(wchar_t* pszDest, const wchar_t* pszSrc);
```

### <a name="remarks"></a>備註

請參閱[PathCanonicalize](/windows/desktop/api/shlwapi/nf-shlwapi-pathcanonicalizea)如需詳細資訊。

## <a name="combine"></a> ATLPath::Combine

此函式是多載包裝函式[PathCombine](/windows/desktop/api/shlwapi/nf-shlwapi-pathcombinea)。

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

如需詳細資訊，請參閱 PathCombine。

## <a name="commonprefix"></a> ATLPath::CommonPrefix

此函式是多載包裝函式[PathCommonPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathcommonprefixa)。

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

請參閱[PathCommonPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathcommonprefixa)如需詳細資訊。

## <a name="compactpath"></a> ATLPath::CompactPath

此函式是多載包裝函式[PathCompactPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpatha)。

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

請參閱[PathCompactPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpatha)如需詳細資訊。

## <a name="compactpathex"></a> ATLPath::CompactPathEx

此函式是多載包裝函式[PathCompactPathEx](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpathexa)。

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

請參閱[PathCompactPathEx](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpathexa)如需詳細資訊。

## <a name="fileexists"></a> ATLPath::FileExists

此函式是多載包裝函式[PathFileExists](/windows/desktop/api/shlwapi/nf-shlwapi-pathfileexistsa)。

### <a name="syntax"></a>語法

```
inline BOOL FileExists(const char* pszPath);
inline BOOL FileExists(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

請參閱[PathFileExists](/windows/desktop/api/shlwapi/nf-shlwapi-pathfileexistsa)如需詳細資訊。

## <a name="findextension"></a> ATLPath::FindExtension

此函式是多載包裝函式[PathFindExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindextensiona)。

### <a name="syntax"></a>語法

```
inline char* FindExtension(const char* pszPath);
inline wchar_t* FindExtension(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

請參閱[PathFindExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindextensiona)如需詳細資訊。

## <a name="findfilename"></a> ATLPath::FindFileName

此函式是多載包裝函式[PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea)。

### <a name="syntax"></a>語法

```
inline char* FindFileName(const char* pszPath);
inline wchar_t* FindFileName(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

請參閱[PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea)如需詳細資訊。

## <a name="getdrivenumber"></a> ATLPath::GetDriveNumber

此函式是多載包裝函式[PathGetDriveNumber](/windows/desktop/api/shlwapi/nf-shlwapi-pathgetdrivenumbera)。

### <a name="syntax"></a>語法

```
inline int GetDriveNumber(const char* pszPath);
inline int GetDriveNumber(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

請參閱[PathGetDriveNumber](/windows/desktop/api/shlwapi/nf-shlwapi-pathgetdrivenumbera)如需詳細資訊。

## <a name="isdirectory"></a>  ATLPath::IsDirectory

此函式是多載包裝函式[PathIsDirectory](/windows/desktop/api/shlwapi/nf-shlwapi-pathisdirectorya)。

```
inline BOOL IsDirectory(const char* pszPath);
inline BOOL IsDirectory(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 PathIsDirectory。

## <a name="isfilespec"></a> ATLPath::IsFileSpec

此函式是多載包裝函式[PathIsFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathisfilespeca)。

### <a name="syntax"></a>語法

```
inline BOOL IsFileSpec(const char* pszPath);
inline BOOL IsFileSpec(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

請參閱[PathIsFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathisfilespeca)如需詳細資訊。

## <a name="isprefix"></a> ATLPath::IsPrefix

此函式是多載包裝函式[PathIsPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathisprefixa)。

### <a name="syntax"></a>語法

```
inline BOOL IsPrefix(const char* pszPrefix, const char* pszPath);
inline BOOL IsPrefix(const wchar_t* pszPrefix, const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

請參閱[PathIsPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathisprefixa)如需詳細資訊。

## <a name="isrelative"></a> ATLPath::IsRelative

此函式是多載包裝函式[PathIsRelative](/windows/desktop/api/shlwapi/nf-shlwapi-pathisrelativea)。

### <a name="syntax"></a>語法

```
inline BOOL IsRelative(const char* pszPath);
inline BOOL IsRelative(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

請參閱[PathIsRelative](/windows/desktop/api/shlwapi/nf-shlwapi-pathisrelativea)如需詳細資訊。

## <a name="isroot"></a> ATLPath::IsRoot

此函式是多載包裝函式[PathIsRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathisroota)。

### <a name="syntax"></a>語法

```
inline BOOL IsRoot(const char* pszPath);
inline BOOL IsRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

請參閱[PathIsRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathisroota)如需詳細資訊。

## <a name="issameroot"></a> ATLPath::IsSameRoot

此函式是多載包裝函式[PathIsSameRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathissameroota)。

### <a name="syntax"></a>語法

```
inline BOOL IsSameRoot(const char* pszPath1, const char* pszPath2);
inline BOOL IsSameRoot(const wchar_t* pszPath1, const wchar_t* pszPath2);
```

### <a name="remarks"></a>備註

請參閱[PathIsSameRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathissameroota)如需詳細資訊。

## <a name="isunc"></a> ATLPath::IsUNC

此函式是多載包裝函式[PathIsUNC](/windows/desktop/api/shlwapi/nf-shlwapi-pathisunca)。

### <a name="syntax"></a>語法

```
inline BOOL IsUNC(const char* pszPath);
inline BOOL IsUNC(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

請參閱[PathIsUNC](/windows/desktop/api/shlwapi/nf-shlwapi-pathisunca)如需詳細資訊。

## <a name="isuncserver"></a> ATLPath::IsUNCServer

此函式是多載包裝函式[PathIsUNCServer](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncservera)。

### <a name="syntax"></a>語法

```
inline BOOL IsUNCServer(const char* pszPath);
inline BOOL IsUNCServer(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

請參閱[PathIsUNCServer](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncservera)如需詳細資訊。

## <a name="isuncservershare"></a> ATLPath::IsUNCServerShare

此函式是多載包裝函式[PathIsUNCServerShare](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncserversharea)。

### <a name="syntax"></a>語法

```
inline BOOL IsUNCServerShare(const char* pszPath);
inline BOOL IsUNCServerShare(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

請參閱[PathIsUNCServerShare](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncserversharea)如需詳細資訊。

## <a name="makepretty"></a> ATLPath::MakePretty

此函式是多載包裝函式[PathMakePretty](/windows/desktop/api/shlwapi/nf-shlwapi-pathmakeprettya)。

### <a name="syntax"></a>語法

```
inline BOOL MakePretty(char* pszPath);
inline BOOL MakePretty(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

請參閱[PathMakePretty](/windows/desktop/api/shlwapi/nf-shlwapi-pathmakeprettya)如需詳細資訊。

## <a name="matchspec"></a> ATLPath::MatchSpec

此函式是多載包裝函式[PathMatchSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathmatchspeca)。

### <a name="syntax"></a>語法

```
inline BOOL MatchSpec(const char* pszPath, const char* pszSpec);
inline BOOL MatchSpec(const wchar_t* pszPath, const wchar_t* pszSpec);
```

### <a name="remarks"></a>備註

請參閱[PathMatchSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathmatchspeca)如需詳細資訊。

## <a name="quotespaces"></a> ATLPath::QuoteSpaces

此函式是多載包裝函式[PathQuoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathquotespacesa)。

### <a name="syntax"></a>語法

```
inline void QuoteSpaces(char* pszPath);
inline void QuoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

請參閱[PathQuoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathquotespacesa)如需詳細資訊。

## <a name="relativepathto"></a> ATLPath::RelativePathTo

此函式是多載包裝函式[PathRelativePathTo](/windows/desktop/api/shlwapi/nf-shlwapi-pathrelativepathtoa)。

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

請參閱[PathRelativePathTo](/windows/desktop/api/shlwapi/nf-shlwapi-pathrelativepathtoa)如需詳細資訊。

## <a name="removeargs"></a> ATLPath::RemoveArgs

此函式是多載包裝函式[PathRemoveArgs](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveargsa)。

### <a name="syntax"></a>語法

```
inline void RemoveArgs(char* pszPath);
inline void RemoveArgs(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

請參閱[PathRemoveArgs](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveargsa)如需詳細資訊。

## <a name="removebackslash"></a> ATLPath::RemoveBackslash

此函式是多載包裝函式[PathRemoveBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovebackslasha)。

### <a name="syntax"></a>語法

```
inline char* RemoveBackslash(char* pszPath);
inline wchar_t* RemoveBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

請參閱[PathRemoveBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovebackslasha)如需詳細資訊。

## <a name="removeblanks"></a> ATLPath::RemoveBlanks

此函式是多載包裝函式[PathRemoveBlanks](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveblanksa)。

### <a name="syntax"></a>語法

```
inline void RemoveBlanks(char* pszPath);
inline void RemoveBlanks(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

請參閱[PathRemoveBlanks](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveblanksa)如需詳細資訊。

## <a name="removeextension"></a> ATLPath::RemoveExtension

此函式是多載包裝函式[PathRemoveExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveextensiona)。

### <a name="syntax"></a>語法

```
inline void RemoveExtension(char* pszPath);
inline void RemoveExtension(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

請參閱[PathRemoveExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveextensiona)如需詳細資訊。

## <a name="removefilespec"></a> ATLPath::RemoveFileSpec

此函式是多載包裝函式[PathRemoveFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovefilespeca)。

### <a name="syntax"></a>語法

```
inline BOOL RemoveFileSpec(char* pszPath);
inline BOOL RemoveFileSpec(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

請參閱[PathRemoveFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovefilespeca)如需詳細資訊。

## <a name="renameextension"></a> ATLPath::RenameExtension

此函式是多載包裝函式[PathRenameExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathrenameextensiona)。

### <a name="syntax"></a>語法

```
inline BOOL RenameExtension(char* pszPath, const char* pszExt);
inline BOOL RenameExtension(wchar_t* pszPath, const wchar_t* pszExt);
```

### <a name="remarks"></a>備註

請參閱[PathRenameExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathrenameextensiona)如需詳細資訊。

## <a name="skiproot"></a> ATLPath::SkipRoot

此函式是多載包裝函式[PathSkipRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathskiproota)。

### <a name="syntax"></a>語法

```
inline char* SkipRoot(const char* pszPath);
inline wchar_t* SkipRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

請參閱[PathSkipRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathskiproota)如需詳細資訊。

## <a name="strippath"></a> ATLPath::StripPath

此函式是多載包裝函式[PathStripPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathstrippatha)。

### <a name="syntax"></a>語法

```
inline void StripPath(char* pszPath);
inline void StripPath(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

請參閱[PathStripPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathstrippatha)如需詳細資訊。

## <a name="striptoroot"></a> ATLPath::StripToRoot

此函式是多載包裝函式[PathStripToRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathstriptoroota)。

### <a name="syntax"></a>語法

```
inline BOOL StripToRoot(char* pszPath);
inline BOOL StripToRoot(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

請參閱[PathStripToRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathstriptoroota)如需詳細資訊。

## <a name="unquotespaces"></a> ATLPath::UnquoteSpaces

此函式是多載包裝函式[PathUnquoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathunquotespacesa)。

### <a name="syntax"></a>語法

```
inline void UnquoteSpaces(char* pszPath);
inline void UnquoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

請參閱[PathUnquoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathunquotespacesa)如需詳細資訊。

