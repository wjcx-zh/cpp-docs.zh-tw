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
ms.openlocfilehash: 76efbb0bd43b800f186eac1afa168fc2a0c939f6
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418185"
---
# <a name="atl-path-functions"></a>ATL 路徑函式

ATL 提供與 atlpath.h 類別來以[CPathT](cpatht-class.md)的形式操作路徑。 這段程式碼可以在與 atlpath.h 中找到。

### <a name="related-classes"></a>相關類別

|||
|-|-|
|[CPathT 類別](cpatht-class.md)|此類別代表路徑。|

### <a name="related-typedefs"></a>相關的 Typedef

|||
|-|-|
|`CPath`|使用 `CString`的特製化[CPathT](cpatht-class.md) 。|
|`CPathA`|使用 `CStringA`的特製化[CPathT](cpatht-class.md) 。|
|`CPathW`|使用 `CStringW`的特製化[CPathT](cpatht-class.md) 。|

### <a name="functions"></a>函式

|||
|-|-|
|[與 atlpath.h：： AddBackslash](#addbackslash)|此函數是[pathaddbackslash 式](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw)的多載包裝函式。|
|[與 atlpath.h：： AddExtension](#addextension)|此函數是[pathaddextension 式](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw)的多載包裝函式。|
|[與 atlpath.h：： Append](#append)|此函數是[pathappend 式](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw)的多載包裝函式。|
|[與 atlpath.h：： BuildRoot](#buildroot)|此函數是[pathbuildroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw)的多載包裝函式。|
|[與 atlpath.h：：正常化](#canonicalize)|此函數是[pathcanonicalize 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew)的多載包裝函式。|
|[與 atlpath.h：：組合](#combine)|此函數是[pathcombine 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew)的多載包裝函式。|
|[與 atlpath.h：： CommonPrefix](#commonprefix)|此函數是[pathcommonprefix 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw)的多載包裝函式。|
|[與 atlpath.h：： CompactPath](#compactpath)|此函數是[pathcompactpath 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw)的多載包裝函式。|
|[與 atlpath.h：： CompactPathEx](#compactpathex)|此函數是[pathcompactpathex 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw)的多載包裝函式。|
|[與 atlpath.h：： FileExists](#fileexists)|此函數是[pathfileexists 式](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw)的多載包裝函式。|
|[與 atlpath.h：： FindExtension](#findextension)|此函數是[pathfindextension 式](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw)的多載包裝函式。|
|[與 atlpath.h：： FindFileName](#findfilename)|此函數是[pathfindfilename 式](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)的多載包裝函式。|
|[與 atlpath.h：： GetDriveNumber](#getdrivenumber)|此函數是[pathgetdrivenumber 式](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw)的多載包裝函式。|
|[與 atlpath.h：： IsDirectory](#isdirectory)|此函數是[pathisdirectory 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw)的多載包裝函式。|
|[與 atlpath.h：： IsFileSpec](#isfilespec)|此函數是[pathisfilespec 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw)的多載包裝函式。|
|[與 atlpath.h：： IsPrefix](#isprefix)|此函數是[pathisprefix 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)的多載包裝函式。|
|[與 atlpath.h：： IsRelative](#isrelative)|此函數是[pathisrelative 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew)的多載包裝函式。|
|[與 atlpath.h：： IsRoot](#isroot)|此函數是[pathisroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw)的多載包裝函式。|
|[與 atlpath.h：： IsSameRoot](#issameroot)|此函數是[pathissameroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw)的多載包裝函式。|
|[與 atlpath.h：： IsUNC](#isunc)|此函數是[pathisunc 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw)的多載包裝函式。|
|[與 atlpath.h：： IsUNCServer](#isuncserver)|此函數是[pathisuncserver 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw)的多載包裝函式。|
|[與 atlpath.h：： IsUNCServerShare](#isuncservershare)|此函數是[pathisuncservershare 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew)的多載包裝函式。|
|[與 atlpath.h：： MakePretty](#makepretty)|此函數是[pathmakepretty 式](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw)的多載包裝函式。|
|[與 atlpath.h：： MatchSpec](#matchspec)|此函數是[pathmatchspec 式](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw)的多載包裝函式。|
|[與 atlpath.h：： QuoteSpaces](#quotespaces)|此函數是[pathquotespaces 式](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw)的多載包裝函式。|
|[與 atlpath.h：： RelativePathTo](#relativepathto)|此函數是[pathrelativepathto 式](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow)的多載包裝函式。|
|[與 atlpath.h：： RemoveArgs](#removeargs)|此函數是[pathremoveargs 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw)的多載包裝函式。|
|[與 atlpath.h：： RemoveBackslash](#removebackslash)|此函數是[pathremovebackslash 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw)的多載包裝函式。|
|[與 atlpath.h：： RemoveBlanks](#removeblanks)|此函數是[pathremoveblanks 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw)的多載包裝函式。|
|[與 atlpath.h：： RemoveExtension](#removeextension)|此函數是[pathremoveextension 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw)的多載包裝函式。|
|[與 atlpath.h：： RemoveFileSpec](#removefilespec)|此函數是[pathremovefilespec 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw)的多載包裝函式。|
|[與 atlpath.h：： RenameExtension](#renameextension)|此函數是[pathrenameextension 式](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw)的多載包裝函式。|
|[與 atlpath.h：： SkipRoot](#skiproot)|此函數是[pathskiproot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw)的多載包裝函式。|
|[與 atlpath.h：： StripPath](#strippath)|此函數是[pathstrippath 式](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw)的多載包裝函式。|
|[與 atlpath.h：： StripToRoot](#striptoroot)|此函數是[pathstriptoroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw)的多載包裝函式。|
|[與 atlpath.h：： UnquoteSpaces](#unquotespaces)|此函數是[pathunquotespaces 式](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw)的多載包裝函式。|

## <a name="requirements"></a>需求

**標頭：** 與 atlpath.h。h

## <a name="addbackslash"></a>與 atlpath.h：： AddBackSlash

此函數是[pathaddbackslash 式](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline char* AddBackslash(char* pszPath);
inline wchar_t* AddBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathaddbackslash 式](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw)。

## <a name="addextension"></a>與 atlpath.h：： AddExtension

此函數是[pathaddextension 式](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline BOOL AddExtension(char* pszPath, const char* pszExtension);
inline BOOL AddExtension(wchar_t* pszPath, const wchar_t* pszExtension);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathaddextension 式](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw)。

## <a name="append"></a>與 atlpath.h：： Append

此函數是[pathappend 式](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline BOOL Append(char* pszPath, const char* pszMore);
inline BOOL Append(wchar_t* pszPath, const wchar_t* pszMore);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathappend 式](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw)。

## <a name="buildroot"></a>與 atlpath.h：： BuildRoot

此函數是[pathbuildroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline char* BuildRoot(char* pszPath, int iDrive);
inline wchar_t* BuildRoot(wchar_t* pszPath, int iDrive);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathbuildroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw)。

## <a name="canonicalize"></a>與 atlpath.h：：正常化

此函數是[pathcanonicalize 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline BOOL Canonicalize(char* pszDest, const char* pszSrc);
inline BOOL Canonicalize(wchar_t* pszDest, const wchar_t* pszSrc);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathcanonicalize 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew)。

## <a name="combine"></a>與 atlpath.h：：組合

此函數是[pathcombine 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew)的多載包裝函式。

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

如需詳細資訊，請參閱 Pathcombine 式。

## <a name="commonprefix"></a>與 atlpath.h：： CommonPrefix

此函數是[pathcommonprefix 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw)的多載包裝函式。

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

如需詳細資訊，請參閱[pathcommonprefix 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw)。

## <a name="compactpath"></a>與 atlpath.h：： CompactPath

此函數是[pathcompactpath 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw)的多載包裝函式。

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

如需詳細資訊，請參閱[pathcompactpath 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw)。

## <a name="compactpathex"></a>與 atlpath.h：： CompactPathEx

此函數是[pathcompactpathex 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw)的多載包裝函式。

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

如需詳細資訊，請參閱[pathcompactpathex 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw)。

## <a name="fileexists"></a>與 atlpath.h：： FileExists

此函數是[pathfileexists 式](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline BOOL FileExists(const char* pszPath);
inline BOOL FileExists(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathfileexists 式](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw)。

## <a name="findextension"></a>與 atlpath.h：： FindExtension

此函數是[pathfindextension 式](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline char* FindExtension(const char* pszPath);
inline wchar_t* FindExtension(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathfindextension 式](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw)。

## <a name="findfilename"></a>與 atlpath.h：： FindFileName

此函數是[pathfindfilename 式](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline char* FindFileName(const char* pszPath);
inline wchar_t* FindFileName(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathfindfilename 式](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)。

## <a name="getdrivenumber"></a>與 atlpath.h：： GetDriveNumber

此函數是[pathgetdrivenumber 式](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline int GetDriveNumber(const char* pszPath);
inline int GetDriveNumber(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathgetdrivenumber 式](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw)。

## <a name="isdirectory"></a>與 atlpath.h：： IsDirectory

此函數是[pathisdirectory 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw)的多載包裝函式。

```
inline BOOL IsDirectory(const char* pszPath);
inline BOOL IsDirectory(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 Pathisdirectory 式。

## <a name="isfilespec"></a>與 atlpath.h：： IsFileSpec

此函數是[pathisfilespec 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline BOOL IsFileSpec(const char* pszPath);
inline BOOL IsFileSpec(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathisfilespec 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw)。

## <a name="isprefix"></a>與 atlpath.h：： IsPrefix

此函數是[pathisprefix 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline BOOL IsPrefix(const char* pszPrefix, const char* pszPath);
inline BOOL IsPrefix(const wchar_t* pszPrefix, const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathisprefix 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)。

## <a name="isrelative"></a>與 atlpath.h：： IsRelative

此函數是[pathisrelative 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline BOOL IsRelative(const char* pszPath);
inline BOOL IsRelative(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathisrelative 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew)。

## <a name="isroot"></a>與 atlpath.h：： IsRoot

此函數是[pathisroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline BOOL IsRoot(const char* pszPath);
inline BOOL IsRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathisroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw)。

## <a name="issameroot"></a>與 atlpath.h：： IsSameRoot

此函數是[pathissameroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline BOOL IsSameRoot(const char* pszPath1, const char* pszPath2);
inline BOOL IsSameRoot(const wchar_t* pszPath1, const wchar_t* pszPath2);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathissameroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw)。

## <a name="isunc"></a>與 atlpath.h：： IsUNC

此函數是[pathisunc 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline BOOL IsUNC(const char* pszPath);
inline BOOL IsUNC(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathisunc 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw)。

## <a name="isuncserver"></a>與 atlpath.h：： IsUNCServer

此函數是[pathisuncserver 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline BOOL IsUNCServer(const char* pszPath);
inline BOOL IsUNCServer(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathisuncserver 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw)。

## <a name="isuncservershare"></a>與 atlpath.h：： IsUNCServerShare

此函數是[pathisuncservershare 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline BOOL IsUNCServerShare(const char* pszPath);
inline BOOL IsUNCServerShare(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathisuncservershare 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew)。

## <a name="makepretty"></a>與 atlpath.h：： MakePretty

此函數是[pathmakepretty 式](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline BOOL MakePretty(char* pszPath);
inline BOOL MakePretty(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathmakepretty 式](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw)。

## <a name="matchspec"></a>與 atlpath.h：： MatchSpec

此函數是[pathmatchspec 式](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline BOOL MatchSpec(const char* pszPath, const char* pszSpec);
inline BOOL MatchSpec(const wchar_t* pszPath, const wchar_t* pszSpec);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathmatchspec 式](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw)。

## <a name="quotespaces"></a>與 atlpath.h：： QuoteSpaces

此函數是[pathquotespaces 式](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline void QuoteSpaces(char* pszPath);
inline void QuoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathquotespaces 式](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw)。

## <a name="relativepathto"></a>與 atlpath.h：： RelativePathTo

此函數是[pathrelativepathto 式](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow)的多載包裝函式。

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

如需詳細資訊，請參閱[pathrelativepathto 式](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow)。

## <a name="removeargs"></a>與 atlpath.h：： RemoveArgs

此函數是[pathremoveargs 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline void RemoveArgs(char* pszPath);
inline void RemoveArgs(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathremoveargs 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw)。

## <a name="removebackslash"></a>與 atlpath.h：： RemoveBackslash

此函數是[pathremovebackslash 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline char* RemoveBackslash(char* pszPath);
inline wchar_t* RemoveBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathremovebackslash 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw)。

## <a name="removeblanks"></a>與 atlpath.h：： RemoveBlanks

此函數是[pathremoveblanks 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline void RemoveBlanks(char* pszPath);
inline void RemoveBlanks(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathremoveblanks 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw)。

## <a name="removeextension"></a>與 atlpath.h：： RemoveExtension

此函數是[pathremoveextension 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline void RemoveExtension(char* pszPath);
inline void RemoveExtension(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathremoveextension 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw)。

## <a name="removefilespec"></a>與 atlpath.h：： RemoveFileSpec

此函數是[pathremovefilespec 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline BOOL RemoveFileSpec(char* pszPath);
inline BOOL RemoveFileSpec(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathremovefilespec 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw)。

## <a name="renameextension"></a>與 atlpath.h：： RenameExtension

此函數是[pathrenameextension 式](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline BOOL RenameExtension(char* pszPath, const char* pszExt);
inline BOOL RenameExtension(wchar_t* pszPath, const wchar_t* pszExt);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathrenameextension 式](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw)。

## <a name="skiproot"></a>與 atlpath.h：： SkipRoot

此函數是[pathskiproot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline char* SkipRoot(const char* pszPath);
inline wchar_t* SkipRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathskiproot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw)。

## <a name="strippath"></a>與 atlpath.h：： StripPath

此函數是[pathstrippath 式](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline void StripPath(char* pszPath);
inline void StripPath(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathstrippath 式](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw)。

## <a name="striptoroot"></a>與 atlpath.h：： StripToRoot

此函數是[pathstriptoroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline BOOL StripToRoot(char* pszPath);
inline BOOL StripToRoot(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathstriptoroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw)。

## <a name="unquotespaces"></a>與 atlpath.h：： UnquoteSpaces

此函數是[pathunquotespaces 式](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw)的多載包裝函式。

### <a name="syntax"></a>語法

```
inline void UnquoteSpaces(char* pszPath);
inline void UnquoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathunquotespaces 式](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw)。
