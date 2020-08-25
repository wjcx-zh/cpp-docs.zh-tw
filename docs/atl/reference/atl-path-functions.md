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
ms.openlocfilehash: e9e8af5a902a51d9a3ee4956a60ad162196f659c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833994"
---
# <a name="atl-path-functions"></a>ATL 路徑函式

ATL 提供 Atlpath.h 類別，可操作 [CPathT](cpatht-class.md)形式的路徑。 您可以在 atlpath.h 中找到此程式碼。

## <a name="related-classes"></a>相關類別

|類別|描述|
|-|-|
|[CPathT 類別](cpatht-class.md)|此類別代表路徑。|

## <a name="related-typedefs"></a>相關的 Typedef

|Typedef|描述|
|-|-|
|`CPath`|使用 [CPathT](cpatht-class.md) 的特製化 `CString` 。|
|`CPathA`|使用 [CPathT](cpatht-class.md) 的特製化 `CStringA` 。|
|`CPathW`|使用 [CPathT](cpatht-class.md) 的特製化 `CStringW` 。|

## <a name="functions"></a>函式

|函式|描述|
|-|-|
|[ATLPath::AddBackslash](#addbackslash)|此函數是 [pathaddbackslash 式](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw)的多載包裝函式。|
|[ATLPath::AddExtension](#addextension)|此函數是 [pathaddextension 式](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw)的多載包裝函式。|
|[ATLPath::Append](#append)|此函數是 [pathappend 式](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw)的多載包裝函式。|
|[ATLPath::BuildRoot](#buildroot)|此函數是 [pathbuildroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw)的多載包裝函式。|
|[ATLPath::Canonicalize](#canonicalize)|此函數是 [pathcanonicalize 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew)的多載包裝函式。|
|[ATLPath::Combine](#combine)|此函數是 [pathcombine 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew)的多載包裝函式。|
|[ATLPath::CommonPrefix](#commonprefix)|此函數是 [pathcommonprefix 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw)的多載包裝函式。|
|[ATLPath::CompactPath](#compactpath)|此函數是 [pathcompactpath 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw)的多載包裝函式。|
|[ATLPath::CompactPathEx](#compactpathex)|此函數是 [pathcompactpathex 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw)的多載包裝函式。|
|[ATLPath::FileExists](#fileexists)|此函數是 [pathfileexists 式](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw)的多載包裝函式。|
|[ATLPath::FindExtension](#findextension)|此函數是 [pathfindextension 式](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw)的多載包裝函式。|
|[ATLPath::FindFileName](#findfilename)|此函數是 [pathfindfilename 式](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)的多載包裝函式。|
|[ATLPath::GetDriveNumber](#getdrivenumber)|此函數是 [pathgetdrivenumber 式](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw)的多載包裝函式。|
|[ATLPath::IsDirectory](#isdirectory)|此函數是 [pathisdirectory 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw)的多載包裝函式。|
|[ATLPath::IsFileSpec](#isfilespec)|此函數是 [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw)的多載包裝函式。|
|[ATLPath::IsPrefix](#isprefix)|此函數是 [pathisprefix 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)的多載包裝函式。|
|[ATLPath::IsRelative](#isrelative)|此函數是 [pathisrelative 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew)的多載包裝函式。|
|[ATLPath::IsRoot](#isroot)|此函數是 [pathisroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw)的多載包裝函式。|
|[ATLPath::IsSameRoot](#issameroot)|此函數是 [pathissameroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw)的多載包裝函式。|
|[ATLPath::IsUNC](#isunc)|此函數是 [pathisunc 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw)的多載包裝函式。|
|[ATLPath::IsUNCServer](#isuncserver)|此函數是 [pathisuncserver 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw)的多載包裝函式。|
|[ATLPath::IsUNCServerShare](#isuncservershare)|此函數是 [pathisuncservershare 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew)的多載包裝函式。|
|[ATLPath::MakePretty](#makepretty)|此函數是 [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw)的多載包裝函式。|
|[ATLPath::MatchSpec](#matchspec)|此函數是 [pathmatchspec 式](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw)的多載包裝函式。|
|[ATLPath::QuoteSpaces](#quotespaces)|此函數是 [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw)的多載包裝函式。|
|[ATLPath::RelativePathTo](#relativepathto)|此函數是 [pathrelativepathto 式](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow)的多載包裝函式。|
|[ATLPath::RemoveArgs](#removeargs)|此函數是 [pathremoveargs 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw)的多載包裝函式。|
|[ATLPath::RemoveBackslash](#removebackslash)|此函數是 [pathremovebackslash 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw)的多載包裝函式。|
|[ATLPath::RemoveBlanks](#removeblanks)|此函數是 [pathremoveblanks 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw)的多載包裝函式。|
|[ATLPath::RemoveExtension](#removeextension)|此函數是 [pathremoveextension 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw)的多載包裝函式。|
|[ATLPath::RemoveFileSpec](#removefilespec)|此函數是 [pathremovefilespec 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw)的多載包裝函式。|
|[ATLPath::RenameExtension](#renameextension)|此函數是 [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw)的多載包裝函式。|
|[ATLPath::SkipRoot](#skiproot)|此函數是 [pathskiproot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw)的多載包裝函式。|
|[ATLPath::StripPath](#strippath)|此函數是 [pathstrippath 式](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw)的多載包裝函式。|
|[ATLPath::StripToRoot](#striptoroot)|此函數是 [pathstriptoroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw)的多載包裝函式。|
|[ATLPath::UnquoteSpaces](#unquotespaces)|此函數是 [pathunquotespaces 式](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw)的多載包裝函式。|

## <a name="requirements"></a>規格需求

**標頭：** atlpath.h。h

## <a name="atlpathaddbackslash"></a><a name="addbackslash"></a> Atlpath.h：： AddBackSlash

此函數是 [pathaddbackslash 式](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline char* AddBackslash(char* pszPath);
inline wchar_t* AddBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [pathaddbackslash 式](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw) 。

## <a name="atlpathaddextension"></a><a name="addextension"></a> Atlpath.h：： AddExtension

此函數是 [pathaddextension 式](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline BOOL AddExtension(char* pszPath, const char* pszExtension);
inline BOOL AddExtension(wchar_t* pszPath, const wchar_t* pszExtension);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [pathaddextension 式](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw) 。

## <a name="atlpathappend"></a><a name="append"></a> Atlpath.h：： Append

此函數是 [pathappend 式](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline BOOL Append(char* pszPath, const char* pszMore);
inline BOOL Append(wchar_t* pszPath, const wchar_t* pszMore);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [pathappend 式](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw) 。

## <a name="atlpathbuildroot"></a><a name="buildroot"></a> Atlpath.h：： >buildroot

此函數是 [pathbuildroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline char* BuildRoot(char* pszPath, int iDrive);
inline wchar_t* BuildRoot(wchar_t* pszPath, int iDrive);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [pathbuildroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw) 。

## <a name="atlpathcanonicalize"></a><a name="canonicalize"></a> Atlpath.h：：正常化

此函數是 [pathcanonicalize 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline BOOL Canonicalize(char* pszDest, const char* pszSrc);
inline BOOL Canonicalize(wchar_t* pszDest, const wchar_t* pszSrc);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [pathcanonicalize 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew) 。

## <a name="atlpathcombine"></a><a name="combine"></a> Atlpath.h：：組合

此函數是 [pathcombine 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
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

如需詳細資訊，請參閱 Pathcombine 式。

## <a name="atlpathcommonprefix"></a><a name="commonprefix"></a> Atlpath.h：： CommonPrefix

此函數是 [pathcommonprefix 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
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

如需詳細資訊，請參閱 [pathcommonprefix 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw) 。

## <a name="atlpathcompactpath"></a><a name="compactpath"></a> Atlpath.h：： CompactPath

此函數是 [pathcompactpath 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
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

如需詳細資訊，請參閱 [pathcompactpath 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw) 。

## <a name="atlpathcompactpathex"></a><a name="compactpathex"></a> Atlpath.h：： CompactPathEx

此函數是 [pathcompactpathex 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
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

如需詳細資訊，請參閱 [pathcompactpathex 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw) 。

## <a name="atlpathfileexists"></a><a name="fileexists"></a> Atlpath.h：： FileExists

此函數是 [pathfileexists 式](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline BOOL FileExists(const char* pszPath);
inline BOOL FileExists(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [pathfileexists 式](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw) 。

## <a name="atlpathfindextension"></a><a name="findextension"></a> Atlpath.h：： FindExtension

此函數是 [pathfindextension 式](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline char* FindExtension(const char* pszPath);
inline wchar_t* FindExtension(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [pathfindextension 式](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw) 。

## <a name="atlpathfindfilename"></a><a name="findfilename"></a> Atlpath.h：： FindFileName

此函數是 [pathfindfilename 式](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline char* FindFileName(const char* pszPath);
inline wchar_t* FindFileName(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [pathfindfilename 式](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew) 。

## <a name="atlpathgetdrivenumber"></a><a name="getdrivenumber"></a> Atlpath.h：： GetDriveNumber

此函數是 [pathgetdrivenumber 式](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline int GetDriveNumber(const char* pszPath);
inline int GetDriveNumber(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [pathgetdrivenumber 式](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw) 。

## <a name="atlpathisdirectory"></a><a name="isdirectory"></a> Atlpath.h：： IsDirectory

此函數是 [pathisdirectory 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw)的多載包裝函式。

```cpp
inline BOOL IsDirectory(const char* pszPath);
inline BOOL IsDirectory(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 Pathisdirectory 式。

## <a name="atlpathisfilespec"></a><a name="isfilespec"></a> Atlpath.h：： IsFileSpec

此函數是 [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline BOOL IsFileSpec(const char* pszPath);
inline BOOL IsFileSpec(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw) 。

## <a name="atlpathisprefix"></a><a name="isprefix"></a> Atlpath.h：： IsPrefix

此函數是 [pathisprefix 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline BOOL IsPrefix(const char* pszPrefix, const char* pszPath);
inline BOOL IsPrefix(const wchar_t* pszPrefix, const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [pathisprefix 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw) 。

## <a name="atlpathisrelative"></a><a name="isrelative"></a> Atlpath.h：： IsRelative

此函數是 [pathisrelative 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline BOOL IsRelative(const char* pszPath);
inline BOOL IsRelative(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [pathisrelative 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew) 。

## <a name="atlpathisroot"></a><a name="isroot"></a> Atlpath.h：： IsRoot

此函數是 [pathisroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline BOOL IsRoot(const char* pszPath);
inline BOOL IsRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [pathisroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw) 。

## <a name="atlpathissameroot"></a><a name="issameroot"></a> Atlpath.h：： IsSameRoot

此函數是 [pathissameroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline BOOL IsSameRoot(const char* pszPath1, const char* pszPath2);
inline BOOL IsSameRoot(const wchar_t* pszPath1, const wchar_t* pszPath2);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [pathissameroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw) 。

## <a name="atlpathisunc"></a><a name="isunc"></a> Atlpath.h：： IsUNC

此函數是 [pathisunc 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline BOOL IsUNC(const char* pszPath);
inline BOOL IsUNC(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [pathisunc 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw) 。

## <a name="atlpathisuncserver"></a><a name="isuncserver"></a> Atlpath.h：： IsUNCServer

此函數是 [pathisuncserver 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline BOOL IsUNCServer(const char* pszPath);
inline BOOL IsUNCServer(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [pathisuncserver 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw) 。

## <a name="atlpathisuncservershare"></a><a name="isuncservershare"></a> Atlpath.h：： IsUNCServerShare

此函數是 [pathisuncservershare 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline BOOL IsUNCServerShare(const char* pszPath);
inline BOOL IsUNCServerShare(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [pathisuncservershare 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew) 。

## <a name="atlpathmakepretty"></a><a name="makepretty"></a> Atlpath.h：： MakePretty

此函數是 [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline BOOL MakePretty(char* pszPath);
inline BOOL MakePretty(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw) 。

## <a name="atlpathmatchspec"></a><a name="matchspec"></a> Atlpath.h：： MatchSpec

此函數是 [pathmatchspec 式](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline BOOL MatchSpec(const char* pszPath, const char* pszSpec);
inline BOOL MatchSpec(const wchar_t* pszPath, const wchar_t* pszSpec);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [pathmatchspec 式](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw) 。

## <a name="atlpathquotespaces"></a><a name="quotespaces"></a> Atlpath.h：： QuoteSpaces

此函數是 [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline void QuoteSpaces(char* pszPath);
inline void QuoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw) 。

## <a name="atlpathrelativepathto"></a><a name="relativepathto"></a> Atlpath.h：： RelativePathTo

此函數是 [pathrelativepathto 式](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
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

如需詳細資訊，請參閱 [pathrelativepathto 式](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow) 。

## <a name="atlpathremoveargs"></a><a name="removeargs"></a> Atlpath.h：： RemoveArgs

此函數是 [pathremoveargs 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline void RemoveArgs(char* pszPath);
inline void RemoveArgs(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [pathremoveargs 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw) 。

## <a name="atlpathremovebackslash"></a><a name="removebackslash"></a> Atlpath.h：： RemoveBackslash

此函數是 [pathremovebackslash 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline char* RemoveBackslash(char* pszPath);
inline wchar_t* RemoveBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [pathremovebackslash 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw) 。

## <a name="atlpathremoveblanks"></a><a name="removeblanks"></a> Atlpath.h：： RemoveBlanks

此函數是 [pathremoveblanks 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline void RemoveBlanks(char* pszPath);
inline void RemoveBlanks(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [pathremoveblanks 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw) 。

## <a name="atlpathremoveextension"></a><a name="removeextension"></a> Atlpath.h：： RemoveExtension

此函數是 [pathremoveextension 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline void RemoveExtension(char* pszPath);
inline void RemoveExtension(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [pathremoveextension 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw) 。

## <a name="atlpathremovefilespec"></a><a name="removefilespec"></a> Atlpath.h：： RemoveFileSpec

此函數是 [pathremovefilespec 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline BOOL RemoveFileSpec(char* pszPath);
inline BOOL RemoveFileSpec(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [pathremovefilespec 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw) 。

## <a name="atlpathrenameextension"></a><a name="renameextension"></a> Atlpath.h：： RenameExtension

此函數是 [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline BOOL RenameExtension(char* pszPath, const char* pszExt);
inline BOOL RenameExtension(wchar_t* pszPath, const wchar_t* pszExt);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw) 。

## <a name="atlpathskiproot"></a><a name="skiproot"></a> Atlpath.h：： SkipRoot

此函數是 [pathskiproot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline char* SkipRoot(const char* pszPath);
inline wchar_t* SkipRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [pathskiproot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw) 。

## <a name="atlpathstrippath"></a><a name="strippath"></a> Atlpath.h：： StripPath

此函數是 [pathstrippath 式](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline void StripPath(char* pszPath);
inline void StripPath(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [pathstrippath 式](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw) 。

## <a name="atlpathstriptoroot"></a><a name="striptoroot"></a> Atlpath.h：： StripToRoot

此函數是 [pathstriptoroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline BOOL StripToRoot(char* pszPath);
inline BOOL StripToRoot(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [pathstriptoroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw) 。

## <a name="atlpathunquotespaces"></a><a name="unquotespaces"></a> Atlpath.h：： UnquoteSpaces

此函數是 [pathunquotespaces 式](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw)的多載包裝函式。

### <a name="syntax"></a>語法

```cpp
inline void UnquoteSpaces(char* pszPath);
inline void UnquoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [pathunquotespaces 式](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw) 。
