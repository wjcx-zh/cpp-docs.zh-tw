---
title: "ATL 路徑函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
keywords:
- "ATL、 路徑"
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a0540fe70464e8c7997275d99d8242e62625bdec
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="atl-path-functions"></a>ATL 路徑函式

ATL 提供 ATLPath 類別操作的表單中的路徑[CPathT](cpatht-class.md)。 此程式碼位於 atlpath.h。  
  
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
|[ATLPath::AddBackslash](#addbackslash)|此函式是多載包裝函式[PathAddBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773561)。|  
|[ATLPath::AddExtension](#addextension)|此函式是多載包裝函式[PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563)。|  
|[ATLPath::Append](#append)|此函式是多載包裝函式[PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565)。|  
|[ATLPath::BuildRoot](#buildroot)|此函式是多載包裝函式[PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567)。|  
|[ATLPath::Canonicalize](#canonicalize)|此函式是多載包裝函式[PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569)。|  
|[ATLPath::Combine](#combine)|此函式是多載包裝函式[PathCombine](http://msdn.microsoft.com/library/windows/desktop/bb773571)。|  
|[ATLPath::CommonPrefix](#commonprefix)|此函式是多載包裝函式[PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574)。|  
|[ATLPath::CompactPath](#compactpath)|此函式是多載包裝函式[PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575)。|  
|[ATLPath::CompactPathEx](#compactpathex)|此函式是多載包裝函式[PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578)。|  
|[ATLPath::FileExists](#fileexists)|此函式是多載包裝函式[PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584)。|  
|[ATLPath::FindExtension](#findextension)|此函式是多載包裝函式[PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587)。|  
|[ATLPath::FindFileName](#findfilename)|此函式是多載包裝函式[PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589)。|  
|[ATLPath::GetDriveNumber](#getdrivenumber)|此函式是多載包裝函式[PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612)。|  
|[ATLPath::IsDirectory](#isdirectory)|此函式是多載包裝函式[PathIsDirectory](http://msdn.microsoft.com/library/windows/desktop/bb773621)。|  
|[ATLPath::IsFileSpec](#isfilespec)|此函式是多載包裝函式[PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627)。|  
|[ATLPath::IsPrefix](#isprefix)|此函式是多載包裝函式[PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650)。|  
|[ATLPath::IsRelative](#isrelative)|此函式是多載包裝函式[PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660)。|  
|[ATLPath::IsRoot](#isroot)|此函式是多載包裝函式[PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674)。|  
|[ATLPath::IsSameRoot](#issameroot)|此函式是多載包裝函式[PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687)。|  
|[ATLPath::IsUNC](#isunc)|此函式是多載包裝函式[PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712)。|  
|[ATLPath::IsUNCServer](#isuncserver)|此函式是多載包裝函式[PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722)。|  
|[ATLPath::IsUNCServerShare](#isuncservershare)|此函式是多載包裝函式[PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723)。|  
|[ATLPath::MakePretty](#makepretty)|此函式是多載包裝函式[PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725)。|  
|[ATLPath::MatchSpec](#matchspec)|此函式是多載包裝函式[PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727)。|  
|[ATLPath::QuoteSpaces](#quotespaces)|此函式是多載包裝函式[PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739)。|  
|[ATLPath::RelativePathTo](#relativepathto)|此函式是多載包裝函式[PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740)。|  
|[ATLPath::RemoveArgs](#removeargs)|此函式是多載包裝函式[PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742)。|  
|[ATLPath::RemoveBackslash](#removebackslash)|此函式是多載包裝函式[PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743)。|  
|[ATLPath::RemoveBlanks](#removeblanks)|此函式是多載包裝函式[PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745)。|  
|[ATLPath::RemoveExtension](#removeextension)|此函式是多載包裝函式[PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746)。|  
|[ATLPath::RemoveFileSpec](#removefilespec)|此函式是多載包裝函式[PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748)。|  
|[ATLPath::RenameExtension](#renameextension)|此函式是多載包裝函式[PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749)。|  
|[ATLPath::SkipRoot](#skiproot)|此函式是多載包裝函式[PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754)。|  
|[ATLPath::StripPath](#strippath)|此函式是多載包裝函式[PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756)。|  
|[ATLPath::StripToRoot](#striptoroot)|此函式是多載包裝函式[PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757)。|  
|[ATLPath::UnquoteSpaces](#unquotespaces)|此函式是多載包裝函式[PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763)。|  
  
## <a name="requirements"></a>需求  
 **標頭：** atlpath.h  

## <a name="addbackslash"></a> ATLPath::AddBackSlash

此函式是多載包裝函式[PathAddBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773561)。  
  
### <a name="syntax"></a>語法  
  
```  
inline char* AddBackslash(char* pszPath);  
inline wchar_t* AddBackslash(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathAddBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773561)如需詳細資訊。  
  
 
  

## <a name="addextension"></a> ATLPath::AddExtension
 此函式是多載包裝函式[PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563)。  
  
### <a name="syntax"></a>語法  
  
```  
inline BOOL AddExtension(char* pszPath, const char* pszExtension);  
inline BOOL AddExtension(wchar_t* pszPath, const wchar_t* pszExtension);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563)如需詳細資訊。 
  
## <a name="append"></a> ATLPath::Append
 此函式是多載包裝函式[PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565)。  
  
### <a name="syntax"></a>語法  
  
```  
inline BOOL Append(char* pszPath, const char* pszMore);  
inline BOOL Append(wchar_t* pszPath, const wchar_t* pszMore);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565)如需詳細資訊。  
  
 
  

## <a name="buildroot"></a> ATLPath::BuildRoot
 此函式是多載包裝函式[PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567)。  
  
### <a name="syntax"></a>語法  
  
```  
inline char* BuildRoot(char* pszPath, int iDrive);  
inline wchar_t* BuildRoot(wchar_t* pszPath, int iDrive);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567)如需詳細資訊。  
  
 
  

## <a name="canonicalize"></a> ATLPath::Canonicalize
 此函式是多載包裝函式[PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569)。  
  
### <a name="syntax"></a>語法  
  
```  
inline BOOL Canonicalize(char* pszDest, const char* pszSrc);  
inline BOOL Canonicalize(wchar_t* pszDest, const wchar_t* pszSrc);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569)如需詳細資訊。  
  
 
  

## <a name="combine"></a> ATLPath::Combine 
此函式是多載包裝函式[PathCombine](https://msdn.microsoft.com/en-us/library/windows/desktop/bb773571)。  

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
 此函式是多載包裝函式[PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574)。  
  
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
 請參閱[PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574)如需詳細資訊。  
  
 
  

## <a name="compactpath"></a> ATLPath::CompactPath
 此函式是多載包裝函式[PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575)。  
  
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
 請參閱[PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575)如需詳細資訊。  
  
 
  

## <a name="compactpathex"></a> ATLPath::CompactPathEx
 此函式是多載包裝函式[PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578)。  
  
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
 請參閱[PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578)如需詳細資訊。  
  
 
  

## <a name="fileexists"></a> ATLPath::FileExists
 此函式是多載包裝函式[PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584)。  
  
### <a name="syntax"></a>語法  
  
```  
inline BOOL FileExists(const char* pszPath);  
inline BOOL FileExists(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584)如需詳細資訊。  
  
 
  

## <a name="findextension"></a> ATLPath::FindExtension
 此函式是多載包裝函式[PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587)。  
  
### <a name="syntax"></a>語法  
  
```  
inline char* FindExtension(const char* pszPath);  
inline wchar_t* FindExtension(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587)如需詳細資訊。  
  
 
  

## <a name="findfilename"></a> ATLPath::FindFileName
 此函式是多載包裝函式[PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589)。  
  
### <a name="syntax"></a>語法  
  
```  
inline char* FindFileName(const char* pszPath);  
inline wchar_t* FindFileName(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589)如需詳細資訊。  
  
 
  

## <a name="getdrivenumber"></a> ATLPath::GetDriveNumber  
 此函式是多載包裝函式[PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612)。  
  
### <a name="syntax"></a>語法  
  
```  
inline int GetDriveNumber(const char* pszPath);  
inline int GetDriveNumber(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612)如需詳細資訊。  
  
 


## <a name="isdirectory"></a>  ATLPath::IsDirectory 
此函式是多載包裝函式[PathIsDirectory](https://msdn.microsoft.com/en-us/library/windows/desktop/bb773621)。

```  
inline BOOL IsDirectory(const char* pszPath);
inline BOOL IsDirectory(const wchar_t* pszPath);
```  
### <a name="remarks"></a>備註
如需詳細資訊，請參閱 PathIsDirectory。  

## <a name="isfilespec"></a> ATLPath::IsFileSpec
 此函式是多載包裝函式[PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627)。  
  
### <a name="syntax"></a>語法  
  
```  
inline BOOL IsFileSpec(const char* pszPath);  
inline BOOL IsFileSpec(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627)如需詳細資訊。  
  
 
  

## <a name="isprefix"></a> ATLPath::IsPrefix
 此函式是多載包裝函式[PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650)。  
  
### <a name="syntax"></a>語法  
  
```  
inline BOOL IsPrefix(const char* pszPrefix, const char* pszPath);  
inline BOOL IsPrefix(const wchar_t* pszPrefix, const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650)如需詳細資訊。  
  
 
  

## <a name="isrelative"></a> ATLPath::IsRelative
 此函式是多載包裝函式[PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660)。  
  
### <a name="syntax"></a>語法  
  
```  
inline BOOL IsRelative(const char* pszPath);  
inline BOOL IsRelative(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660)如需詳細資訊。  
  
 
  

## <a name="isroot"></a> ATLPath::IsRoot
 此函式是多載包裝函式[PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674)。  
  
### <a name="syntax"></a>語法  
  
```  
inline BOOL IsRoot(const char* pszPath);  
inline BOOL IsRoot(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674)如需詳細資訊。  
  
 
  

## <a name="issameroot"></a> ATLPath::IsSameRoot
 此函式是多載包裝函式[PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687)。  
  
### <a name="syntax"></a>語法  
  
```  
inline BOOL IsSameRoot(const char* pszPath1, const char* pszPath2);  
inline BOOL IsSameRoot(const wchar_t* pszPath1, const wchar_t* pszPath2);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687)如需詳細資訊。  
  
 
  

## <a name="isunc"></a> ATLPath::IsUNC
 此函式是多載包裝函式[PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712)。  
  
### <a name="syntax"></a>語法  
  
```  
inline BOOL IsUNC(const char* pszPath);  
inline BOOL IsUNC(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712)如需詳細資訊。  
  
 
  

## <a name="isuncserver"></a> ATLPath::IsUNCServer
 此函式是多載包裝函式[PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722)。  
  
### <a name="syntax"></a>語法  
  
```  
inline BOOL IsUNCServer(const char* pszPath);  
inline BOOL IsUNCServer(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722)如需詳細資訊。  
  
 
  

## <a name="isuncservershare"></a> ATLPath::IsUNCServerShare
 此函式是多載包裝函式[PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723)。  
  
### <a name="syntax"></a>語法  
  
```  
inline BOOL IsUNCServerShare(const char* pszPath);  
inline BOOL IsUNCServerShare(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723)如需詳細資訊。  
  
 
  

## <a name="makepretty"></a> ATLPath::MakePretty
 此函式是多載包裝函式[PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725)。  
  
### <a name="syntax"></a>語法  
  
```  
inline BOOL MakePretty(char* pszPath);  
inline BOOL MakePretty(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725)如需詳細資訊。  
  
 
  

## <a name="matchspec"></a> ATLPath::MatchSpec  
 此函式是多載包裝函式[PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727)。  
  
### <a name="syntax"></a>語法  
  
```  
inline BOOL MatchSpec(const char* pszPath, const char* pszSpec);  
inline BOOL MatchSpec(const wchar_t* pszPath, const wchar_t* pszSpec);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727)如需詳細資訊。  
  
 
  

## <a name="quotespaces"></a> ATLPath::QuoteSpaces  
 此函式是多載包裝函式[PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739)。  
  
### <a name="syntax"></a>語法  
  
```  
inline void QuoteSpaces(char* pszPath);  
inline void QuoteSpaces(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739)如需詳細資訊。  
  
 
  

## <a name="relativepathto"></a> ATLPath::RelativePathTo
 此函式是多載包裝函式[PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740)。  
  
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
 請參閱[PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740)如需詳細資訊。  
  
 
  

## <a name="removeargs"></a> ATLPath::RemoveArgs  
 此函式是多載包裝函式[PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742)。  
  
### <a name="syntax"></a>語法  
  
```  
inline void RemoveArgs(char* pszPath);  
inline void RemoveArgs(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742)如需詳細資訊。  
  
 
  

## <a name="removebackslash"></a> ATLPath::RemoveBackslash
 此函式是多載包裝函式[PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743)。  
  
### <a name="syntax"></a>語法  
  
```  
inline char* RemoveBackslash(char* pszPath);  
inline wchar_t* RemoveBackslash(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743)如需詳細資訊。  
  
 
  

## <a name="removeblanks"></a> ATLPath::RemoveBlanks
 此函式是多載包裝函式[PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745)。  
  
### <a name="syntax"></a>語法  
  
```  
inline void RemoveBlanks(char* pszPath);  
inline void RemoveBlanks(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745)如需詳細資訊。  
  
 
  

## <a name="removeextension"></a> ATLPath::RemoveExtension
 此函式是多載包裝函式[PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746)。  
  
### <a name="syntax"></a>語法  
  
```  
inline void RemoveExtension(char* pszPath);  
inline void RemoveExtension(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746)如需詳細資訊。  
  
 
  

## <a name="removefilespec"></a> ATLPath::RemoveFileSpec
 此函式是多載包裝函式[PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748)。  
  
### <a name="syntax"></a>語法  
  
```  
inline BOOL RemoveFileSpec(char* pszPath);  
inline BOOL RemoveFileSpec(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748)如需詳細資訊。  
  
 
  

## <a name="renameextension"></a> ATLPath::RenameExtension
 此函式是多載包裝函式[PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749)。  
  
### <a name="syntax"></a>語法  
  
```  
inline BOOL RenameExtension(char* pszPath, const char* pszExt);  
inline BOOL RenameExtension(wchar_t* pszPath, const wchar_t* pszExt);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749)如需詳細資訊。  
  
 
  

## <a name="skiproot"></a> ATLPath::SkipRoot
 此函式是多載包裝函式[PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754)。  
  
### <a name="syntax"></a>語法  
  
```  
inline char* SkipRoot(const char* pszPath);  
inline wchar_t* SkipRoot(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754)如需詳細資訊。  
  
 
  

## <a name="strippath"></a> ATLPath::StripPath
 此函式是多載包裝函式[PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756)。  
  
### <a name="syntax"></a>語法  
  
```  
inline void StripPath(char* pszPath);  
inline void StripPath(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756)如需詳細資訊。  
  
 
  


## <a name="striptoroot"></a> ATLPath::StripToRoot
 此函式是多載包裝函式[PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757)。  
  
### <a name="syntax"></a>語法  
  
```  
inline BOOL StripToRoot(char* pszPath);  
inline BOOL StripToRoot(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757)如需詳細資訊。  
  
 
  

## <a name="unquotespaces"></a> ATLPath::UnquoteSpaces
 此函式是多載包裝函式[PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763)。  
  
### <a name="syntax"></a>語法  
  
```  
inline void UnquoteSpaces(char* pszPath);  
inline void UnquoteSpaces(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>備註  
 請參閱[PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763)如需詳細資訊。  
  
 
  
 
