---
title: CPathT 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CPathT
- ATLPATH/ATL::CPathT
- ATLPATH/ATL::CPathT::PCXSTR
- ATLPATH/ATL::CPathT::PXSTR
- ATLPATH/ATL::CPathT::XCHAR
- ATLPATH/ATL::CPathT::CPathT
- ATLPATH/ATL::CPathT::AddBackslash
- ATLPATH/ATL::CPathT::AddExtension
- ATLPATH/ATL::CPathT::Append
- ATLPATH/ATL::CPathT::BuildRoot
- ATLPATH/ATL::CPathT::Canonicalize
- ATLPATH/ATL::CPathT::Combine
- ATLPATH/ATL::CPathT::CommonPrefix
- ATLPATH/ATL::CPathT::CompactPath
- ATLPATH/ATL::CPathT::CompactPathEx
- ATLPATH/ATL::CPathT::FileExists
- ATLPATH/ATL::CPathT::FindExtension
- ATLPATH/ATL::CPathT::FindFileName
- ATLPATH/ATL::CPathT::GetDriveNumber
- ATLPATH/ATL::CPathT::GetExtension
- ATLPATH/ATL::CPathT::IsDirectory
- ATLPATH/ATL::CPathT::IsFileSpec
- ATLPATH/ATL::CPathT::IsPrefix
- ATLPATH/ATL::CPathT::IsRelative
- ATLPATH/ATL::CPathT::IsRoot
- ATLPATH/ATL::CPathT::IsSameRoot
- ATLPATH/ATL::CPathT::IsUNC
- ATLPATH/ATL::CPathT::IsUNCServer
- ATLPATH/ATL::CPathT::IsUNCServerShare
- ATLPATH/ATL::CPathT::MakePretty
- ATLPATH/ATL::CPathT::MatchSpec
- ATLPATH/ATL::CPathT::QuoteSpaces
- ATLPATH/ATL::CPathT::RelativePathTo
- ATLPATH/ATL::CPathT::RemoveArgs
- ATLPATH/ATL::CPathT::RemoveBackslash
- ATLPATH/ATL::CPathT::RemoveBlanks
- ATLPATH/ATL::CPathT::RemoveExtension
- ATLPATH/ATL::CPathT::RemoveFileSpec
- ATLPATH/ATL::CPathT::RenameExtension
- ATLPATH/ATL::CPathT::SkipRoot
- ATLPATH/ATL::CPathT::StripPath
- ATLPATH/ATL::CPathT::StripToRoot
- ATLPATH/ATL::CPathT::UnquoteSpaces
- ATLPATH/ATL::CPathT::m_strPath
dev_langs:
- C++
helpviewer_keywords:
- CPathT class
ms.assetid: eba4137d-1fd2-4b44-a2e1-0944db64df3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a953f94e48f3093b1c61a1567252e04d98c1beb8
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43208539"
---
# <a name="cpatht-class"></a>CPathT 類別
此類別代表的路徑。  
  
> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <typename StringType>
class CPathT
```  
  
#### <a name="parameters"></a>參數  
 *StringType*  
 ATL/MFC 字串類別使用的路徑 (請參閱[CStringT](../../atl-mfc-shared/reference/cstringt-class.md))。  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|[CPathT::PCXSTR](#pcxstr)|常數字串型別。|  
|[CPathT::PXSTR](#pxstr)|字串型別。|  
|[CPathT::XCHAR](#xchar)|字元類型。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CPathT::CPathT](#cpatht)|路徑的建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CPathT::AddBackslash](#addbackslash)|呼叫這個方法來建立路徑的正確語法的字串結尾加上反斜線。|  
|[CPathT::AddExtension](#addextension)|呼叫這個方法，將副檔名新增至路徑。|  
|[CPathT::Append](#append)|呼叫這個方法將字串附加至目前的路徑。|  
|[CPathT::BuildRoot](#buildroot)|呼叫這個方法來建立根路徑指定磁碟機數目。|  
|[CPathT::Canonicalize](#canonicalize)|呼叫這個方法將路徑轉換成標準格式。|  
|[CPathT::Combine](#combine)|呼叫這個方法來串連字串，表示目錄名稱和字串，表示為一個路徑的檔案路徑名稱。|  
|[CPathT::CommonPrefix](#commonprefix)|呼叫這個方法來判斷指定的路徑是否共用通用的前置詞，以目前的路徑。|  
|[CPathT::CompactPath](#compactpath)|呼叫這個方法來截斷以符合給定的像素寬度，以省略符號取代路徑元件的檔案路徑。|  
|[CPathT::CompactPathEx](#compactpathex)|呼叫這個方法來截斷以符合指定的字元數，以省略符號取代路徑元件的檔案路徑。|  
|[CPathT::FileExists](#fileexists)|呼叫這個方法來檢查是否位於這個路徑名稱的檔案存在。|  
|[CPathT::FindExtension](#findextension)|呼叫這個方法來尋找檔案的副檔名的路徑內的位置。|  
|[CPathT::FindFileName](#findfilename)|呼叫這個方法來尋找檔案名稱，在該路徑內的位置。|  
|[CPathT::GetDriveNumber](#getdrivenumber)|呼叫這個方法，以搜尋磁碟機代號的 'A' 到 'Z' 範圍內的路徑，並傳回對應的磁碟機數目。|  
|[CPathT::GetExtension](#getextension)|呼叫這個方法，以從路徑取得檔案的副檔名。|  
|[CPathT::IsDirectory](#isdirectory)|呼叫這個方法，以檢查路徑是否有效的目錄。|  
|[CPathT::IsFileSpec](#isfilespec)|呼叫這個方法來搜尋任何路徑分隔字元的路徑 (例如，':' 或 '\\')。 如果不有存在任何路徑分隔字元，路徑會被視為檔案規格的路徑。|  
|[CPathT::IsPrefix](#isprefix)|呼叫這個方法來判斷路徑是否包含有效的首碼，所傳遞之型別的*pszPrefix*。|  
|[CPathT::IsRelative](#isrelative)|呼叫這個方法來判斷這是否為相對路徑。|  
|[CPathT::IsRoot](#isroot)|呼叫這個方法來判斷路徑是否為根目錄。|  
|[CPathT::IsSameRoot](#issameroot)|呼叫這個方法來判斷另一個路徑是否有常見的根元件，以目前的路徑。|  
|[CPathT::IsUNC](#isunc)|呼叫這個方法來判斷路徑是否有效的 UNC （通用命名慣例） 路徑的伺服器和共用。|  
|[CPathT::IsUNCServer](#isuncserver)|呼叫這個方法來判斷路徑是否有效的 UNC （通用命名慣例） 路徑，僅適用於伺服器。|  
|[CPathT::IsUNCServerShare](#isuncservershare)|呼叫這個方法來判斷路徑是否有效的 UNC （通用命名慣例） 共用路徑， \\ \ *伺服器*\ *共用*。|  
|[CPathT::MakePretty](#makepretty)|呼叫這個方法來將路徑轉換成一致的外觀提供路徑的所有小寫字元。|  
|[CPathT::MatchSpec](#matchspec)|呼叫這個方法來搜尋的路徑包含萬用字元的相符項目類型的字串。|  
|[CPathT::QuoteSpaces](#quotespaces)|呼叫這個方法來將路徑括在引號中，如果它包含任何空格。|  
|[CPathT::RelativePathTo](#relativepathto)|呼叫這個方法來建立從一個檔案或資料夾的相對路徑到另一個。|  
|[CPathT::RemoveArgs](#removeargs)|呼叫這個方法，以從路徑移除任何命令列引數。|  
|[CPathT::RemoveBackslash](#removebackslash)|呼叫這個方法，以從路徑移除尾端有反斜線。|  
|[CPathT::RemoveBlanks](#removeblanks)|呼叫這個方法來移除所有開頭和尾端空格的路徑。|  
|[CPathT::RemoveExtension](#removeextension)|如果有的話，請呼叫這個方法，以移除路徑的副檔名。|  
|[CPathT::RemoveFileSpec](#removefilespec)|如果它們，請呼叫這個方法，以從路徑移除尾端的檔案名稱及反斜線。|  
|[CPathT::RenameExtension](#renameextension)|呼叫這個方法來取代新的延伸模組的路徑中的檔案名稱副檔名。 如果檔案名稱不包含延伸模組，擴充功能就會附加至字串結尾。|  
|[CPathT::SkipRoot](#skiproot)|呼叫這個方法來剖析路徑，將忽略磁碟機代號或 UNC 伺服器/共用路徑的任何部分。|  
|[CPathT::StripPath](#strippath)|呼叫這個方法來移除完整的路徑和檔案名稱的路徑部分。|  
|[CPathT::StripToRoot](#striptoroot)|呼叫這個方法來移除所有的部分，除了根資訊的路徑。|  
|[CPathT::UnquoteSpaces](#unquotespaces)|呼叫這個方法來移除開頭和結尾的路徑中的引號。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CPathT::operator const StringType （& s)](#operator_const_stringtype_amp)|此運算子可讓被視為字串的物件。|  
|[CPathT::operator CPathT::PCXSTR](#operator_cpatht__pcxstr)|此運算子可讓被視為字串的物件。|  
|[CPathT::operator StringType （& s)](#operator_stringtype)|此運算子可讓被視為字串的物件。|  
|[CPathT::operator + =](#operator_add_eq)|這個運算子會將字串附加至路徑。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CPathT::m_strPath](#m_strpath)|路徑。|  
  
## <a name="remarks"></a>備註  
 `CPath``CPathA`，並`CPathW`是具現化的`CPathT`定義，如下所示：  
  
 `typedef CPathT< CString > CPath;`  
  
 `typedef CPathT< CStringA > CPathA;`  
  
 `typedef CPathT< CStringW > CPathW;`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlpath.h  
  
##  <a name="addbackslash"></a>  CPathT::AddBackslash  
 呼叫這個方法來建立路徑的正確語法的字串結尾加上反斜線。 如果路徑已經有尾端有反斜線，則會不新增任何反斜線。  
  
```
void AddBackslash();
```  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathAddBackSlash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha)。  
  
##  <a name="addextension"></a>  CPathT::AddExtension  
 呼叫這個方法，將副檔名新增至路徑。  
  
```
BOOL AddExtension(PCXSTR pszExtension);
```  
  
### <a name="parameters"></a>參數  
 *pszExtension*  
 若要新增檔案副檔名。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 TRUE 失敗則為 FALSE。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathAddExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddextensiona)。  
  
##  <a name="append"></a>  CPathT::Append  
 呼叫這個方法將字串附加至目前的路徑。  
  
```
BOOL Append(PCXSTR pszMore);
```  
  
### <a name="parameters"></a>參數  
 *pszMore*  
 要附加的字串。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 TRUE 失敗則為 FALSE。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathAppend](/windows/desktop/api/shlwapi/nf-shlwapi-pathappenda)。  
  
##  <a name="buildroot"></a>  CPathT::BuildRoot  
 呼叫這個方法來建立根路徑指定磁碟機數目。  
  
```
void BuildRoot(int iDrive);
```  
  
### <a name="parameters"></a>參數  
 *iDrive*  
 磁碟機編號 0 是 a: (1 為 b，依此類推）。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathBuildRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathbuildroota)。  
  
##  <a name="canonicalize"></a>  CPathT::Canonicalize  
 呼叫這個方法將路徑轉換成標準格式。  
  
```
void Canonicalize();
```  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathCanonicalize](/windows/desktop/api/shlwapi/nf-shlwapi-pathcanonicalizea)。  
  
##  <a name="combine"></a>  CPathT::Combine  
 呼叫這個方法來串連字串，表示目錄名稱和字串，表示為一個路徑的檔案路徑名稱。  
  
```
void Combine(PCXSTR pszDir, PCXSTR  pszFile);
```  
  
### <a name="parameters"></a>參數  
 *pszDir*  
 目錄路徑。  
  
 *pszFile*  
 檔案路徑。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathCombine](/windows/desktop/api/shlwapi/nf-shlwapi-pathcombinea)。  
  
##  <a name="commonprefix"></a>  CPathT::CommonPrefix  
 呼叫這個方法來判斷指定的路徑是否共用通用的前置詞，以目前的路徑。  
  
```
CPathT<StringType> CommonPrefix(PCXSTR pszOther);
```  
  
### <a name="parameters"></a>參數  
 *pszOther*  
 要比較目前的路徑。  
  
### <a name="return-value"></a>傳回值  
 傳回的一般前置詞。  
  
### <a name="remarks"></a>備註  
 前置詞是其中一種類型:"c:\\\\"，"。"，"..."，"...\\\\". 如需詳細資訊，請參閱 < [PathCommonPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathcommonprefixa)。  
  
##  <a name="compactpath"></a>  CPathT::CompactPath  
 呼叫這個方法來截斷以符合給定的像素寬度，以省略符號取代路徑元件的檔案路徑。  
  
```
BOOL CompactPath(HDC hDC, UINT nWidth);
```  
  
### <a name="parameters"></a>參數  
 *hDC*  
 使用字型度量資訊的裝置內容。  
  
 *nWidth*  
 寬度，單位為像素，字串將會強制放入。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 TRUE 失敗則為 FALSE。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathCompactPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpatha)。  
  
##  <a name="compactpathex"></a>  CPathT::CompactPathEx  
 呼叫這個方法來截斷以符合指定的字元數，以省略符號取代路徑元件的檔案路徑。  
  
```
BOOL CompactPathEx(UINT nMaxChars, DWORD dwFlags = 0);
```  
  
### <a name="parameters"></a>參數  
 *nMaxChars*  
 要包含在新的字串，包含結束的 NULL 字元的字元數目上限。  
  
 *dwFlags*  
 保留的。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 TRUE 失敗則為 FALSE。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathCompactPathEx](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpathexa)。  
  
##  <a name="cpatht"></a>  CPathT::CPathT  
 建構函式。  
  
```
CPathT(PCXSTR pszPath);
CPathT(const CPathT<StringType>& path);
CPathT() throw();
```  
  
### <a name="parameters"></a>參數  
 *pszPath*  
 要將路徑字串的指標。  
  
 *path*  
 路徑字串中。  
  
##  <a name="fileexists"></a>  CPathT::FileExists  
 呼叫這個方法來檢查是否位於這個路徑名稱的檔案存在。  
  
```
BOOL FileExists() const;
```  
  
### <a name="return-value"></a>傳回值  
 為 true，則會傳回檔案是否存在，FALSE 否則。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathFileExists](/windows/desktop/api/shlwapi/nf-shlwapi-pathfileexistsa)。  
  
##  <a name="findextension"></a>  CPathT::FindExtension  
 呼叫這個方法來尋找檔案的副檔名的路徑內的位置。  
  
```
int FindExtension() const;
```  
  
### <a name="return-value"></a>傳回值  
 傳回的位置 」。 「 上述擴充功能。 如果不找到任何延伸模組，則傳回-1。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathFindExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindextensiona)。  
  
##  <a name="findfilename"></a>  CPathT::FindFileName  
 呼叫這個方法來尋找檔案名稱，在該路徑內的位置。  
  
```
int FindFileName() const;
```  
  
### <a name="return-value"></a>傳回值  
 傳回檔案名稱的位置。 如果不找到任何檔案名稱，則傳回-1。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea)。  
  
##  <a name="getdrivenumber"></a>  CPathT::GetDriveNumber  
 呼叫這個方法，以搜尋磁碟機代號的 'A' 到 'Z' 範圍內的路徑，並傳回對應的磁碟機數目。  
  
```
int GetDriveNumber() const;
```  
  
### <a name="return-value"></a>傳回值  
 以整數會傳回磁碟機編號從 0 到 25 （對應至 'A' 到 'Z'） 如果路徑中有磁碟機代號，則為-1 否則。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathGetDriveNumber](/windows/desktop/api/shlwapi/nf-shlwapi-pathgetdrivenumbera)。  
  
##  <a name="getextension"></a>  CPathT::GetExtension  
 呼叫這個方法，以從路徑取得檔案的副檔名。  
  
```
StringType GetExtension() const;
```  
  
### <a name="return-value"></a>傳回值  
 傳回檔案的副檔名。  
  
##  <a name="isdirectory"></a>  CPathT::IsDirectory  
 呼叫這個方法，以檢查路徑是否有效的目錄。  
  
```
BOOL IsDirectory() const;
```  
  
### <a name="return-value"></a>傳回值  
 如果路徑是目錄，而 FALSE 否則會傳回非零值 (16)。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathIsDirectory](/windows/desktop/api/shlwapi/nf-shlwapi-pathisdirectorya)。  
  
##  <a name="isfilespec"></a>  CPathT::IsFileSpec  
 呼叫這個方法來搜尋任何路徑分隔字元的路徑 (例如，':' 或 '\\')。 如果不有存在任何路徑分隔字元，路徑會被視為檔案規格的路徑。  
  
```
BOOL IsFileSpec() const;
```  
  
### <a name="return-value"></a>傳回值  
 如果沒有在該路徑中，路徑分隔字元，則為 TRUE 或 FALSE 路徑分隔字元時傳回。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathIsFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathisfilespeca)。  
  
##  <a name="isprefix"></a>  CPathT::IsPrefix  
 呼叫這個方法來判斷路徑是否包含有效的首碼，所傳遞之型別的*pszPrefix*。  
  
```
BOOL IsPrefix(PCXSTR pszPrefix) const;
```  
  
### <a name="parameters"></a>參數  
 *pszPrefix*  
 要搜尋的前置詞。 前置詞是其中一種類型:"c:\\\\"，"。"，"..."，"...\\\\".  
  
### <a name="return-value"></a>傳回值  
 如果路徑可包含 FALSE 的前置詞，否則，傳回 TRUE。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathIsPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathisprefixa)。  
  
##  <a name="isrelative"></a>  CPathT::IsRelative  
 呼叫這個方法來判斷這是否為相對路徑。  
  
```
BOOL IsRelative() const;
```  
  
### <a name="return-value"></a>傳回值  
 如果路徑是相對或 FALSE 是否絕對會傳回 TRUE。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathIsRelative](/windows/desktop/api/shlwapi/nf-shlwapi-pathisrelativea)。  
  
##  <a name="isroot"></a>  CPathT::IsRoot  
 呼叫這個方法來判斷路徑是否為根目錄。  
  
```
BOOL IsRoot() const;
```  
  
### <a name="return-value"></a>傳回值  
 如果路徑不根或 FALSE，則傳回 TRUE。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathIsRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathisroota)。  
  
##  <a name="issameroot"></a>  CPathT::IsSameRoot  
 呼叫這個方法來判斷另一個路徑是否有常見的根元件，以目前的路徑。  
  
```
BOOL IsSameRoot(PCXSTR pszOther) const;
```  
  
### <a name="parameters"></a>參數  
 *pszOther*  
 在另一個路徑。  
  
### <a name="return-value"></a>傳回值  
 如果這兩個字串可有相同的根元件或 FALSE 否則會傳回 TRUE。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathIsSameRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathissameroota)。  
  
##  <a name="isunc"></a>  CPathT::IsUNC  
 呼叫這個方法來判斷路徑是否有效的 UNC （通用命名慣例） 路徑的伺服器和共用。  
  
```
BOOL IsUNC() const;
```  
  
### <a name="return-value"></a>傳回值  
 如果路徑不是有效的 UNC 路徑或 FALSE，傳回 TRUE。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathIsUNC](/windows/desktop/api/shlwapi/nf-shlwapi-pathisunca)。  
  
##  <a name="isuncserver"></a>  CPathT::IsUNCServer  
 呼叫這個方法來判斷路徑是否有效的 UNC （通用命名慣例） 路徑，僅適用於伺服器。  
  
```
BOOL IsUNCServer() const;
```  
  
### <a name="return-value"></a>傳回值  
 為 true，則會傳回字串是否為有效的 UNC 路徑僅適用於伺服器 （沒有共用名稱） 或 FALSE 否則。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathIsUNCServer](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncservera)。  
  
##  <a name="isuncservershare"></a>  CPathT::IsUNCServerShare  
 呼叫這個方法來判斷路徑是否有效的 UNC （通用命名慣例） 共用路徑， \\ \ *伺服器*\ *共用*。  
  
```
BOOL IsUNCServerShare() const;
```  
  
### <a name="return-value"></a>傳回值  
 會傳回 TRUE，如果路徑是在表單\\ \ *伺服器*\ *共用*，或 FALSE 否則。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathIsUNCServerShare](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncserversharea)。  
  
##  <a name="m_strpath"></a>  CPathT::m_strPath  
 路徑。  
  
```
StringType m_strPath;
```  
  
### <a name="remarks"></a>備註  
 `StringType` 是範本參數`CPathT`。  
  
##  <a name="makepretty"></a>  CPathT::MakePretty  
 呼叫這個方法來將路徑轉換成一致的外觀提供路徑的所有小寫字元。  
  
```
BOOL MakePretty();
```  
  
### <a name="return-value"></a>傳回值  
 否則傳回已轉換路徑，如果為 TRUE 或 FALSE。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathMakePretty](/windows/desktop/api/shlwapi/nf-shlwapi-pathmakeprettya)。  
  
##  <a name="matchspec"></a>  CPathT::MatchSpec  
 呼叫這個方法來搜尋的路徑包含萬用字元的相符項目類型的字串。  
  
```
BOOL MatchSpec(PCXSTR pszSpec) const;
```  
  
### <a name="parameters"></a>參數  
 *pszSpec*  
 要搜尋的檔案類型的 null 終止字串的指標。 例如，若要測試文件檔案，在目前路徑的檔案是否*pszSpec*應該設定為"*.doc"。  
  
### <a name="return-value"></a>傳回值  
 否則傳回的字串符合時，如果為 TRUE 或 FALSE。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathMatchSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathmatchspeca)。  
  
##  <a name="operator_add_eq"></a>  CPathT::operator + =  
 這個運算子會將字串附加至路徑。  
  
```
CPathT<StringType>& operator+=(PCXSTR pszMore);
```  
  
### <a name="parameters"></a>參數  
 *pszMore*  
 要附加的字串。  
  
### <a name="return-value"></a>傳回值  
 傳回已更新的路徑。  
  
##  <a name="operator_const_stringtype_amp"></a>  CPathT::operator const StringType &amp;  
 此運算子可讓被視為字串的物件。  
  
```
 operatorconst StringType&() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回字串，表示目前由這個物件的路徑。  
  
##  <a name="operator_cpatht__pcxstr"></a>  CPathT::operator CPathT::PCXSTR  
 此運算子可讓被視為字串的物件。  
  
```
 operatorPCXSTR() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回字串，表示目前由這個物件的路徑。  
  
##  <a name="operator_stringtype__amp"></a>  CPathT::operator StringType &amp;  
 此運算子可讓被視為字串的物件。  
  
```
 operatorStringType&() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回字串，表示目前由這個物件的路徑。  
  
##  <a name="pcxstr"></a>  CPathT::PCXSTR  
 常數字串型別。  
  
```
typedef StringType::PCXSTR PCXSTR;
```  
  
### <a name="remarks"></a>備註  
 `StringType` 是範本參數`CPathT`。  
  
##  <a name="pxstr"></a>  CPathT::PXSTR  
 字串型別。  
  
```
typedef StringType::PXSTR PXSTR;
```  
  
### <a name="remarks"></a>備註  
 `StringType` 是範本參數`CPathT`。  
  
##  <a name="quotespaces"></a>  CPathT::QuoteSpaces  
 呼叫這個方法來將路徑括在引號中，如果它包含任何空格。  
  
```
void QuoteSpaces();
```  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathQuoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathquotespacesa)。  
  
##  <a name="relativepathto"></a>  CPathT::RelativePathTo  
 呼叫這個方法來建立從一個檔案或資料夾的相對路徑到另一個。  
  
```
BOOL RelativePathTo(
    PCXSTR pszFrom,
    DWORD dwAttrFrom,
    PCXSTR pszTo,
    DWORD dwAttrTo);
```  
  
### <a name="parameters"></a>參數  
 *pszFrom*  
 相對路徑的起點。  
  
 *dwAttrFrom*  
 檔案屬性*pszFrom*。 如果這個值包含 FILE_ATTRIBUTE_DIRECTORY， *pszFrom*假設是目錄，否則*pszFrom*假設為檔案。  
  
 *pszTo*  
 相對路徑的結束點。  
  
 *dwAttrTo*  
 檔案屬性*pszTo*。 如果這個值包含 FILE_ATTRIBUTE_DIRECTORY， *pszTo*假設是目錄，否則*pszTo*假設為檔案。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 TRUE 失敗則為 FALSE。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathRelativePathTo](/windows/desktop/api/shlwapi/nf-shlwapi-pathrelativepathtoa)。  
  
##  <a name="removeargs"></a>  CPathT::RemoveArgs  
 呼叫這個方法，以從路徑移除任何命令列引數。  
  
```
void RemoveArgs();
```  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathRemoveArgs](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveargsa)。  
  
##  <a name="removebackslash"></a>  CPathT::RemoveBackslash  
 呼叫這個方法，以從路徑移除尾端有反斜線。  
  
```
void RemoveBackslash();
```  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathRemoveBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovebackslasha)。  
  
##  <a name="removeblanks"></a>  CPathT::RemoveBlanks  
 呼叫這個方法來移除所有開頭和尾端空格的路徑。  
  
```
void RemoveBlanks();
```  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathRemoveBlanks](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveblanksa)。  
  
##  <a name="removeextension"></a>  CPathT::RemoveExtension  
 如果有的話，請呼叫這個方法，以移除路徑的副檔名。  
  
```
void RemoveExtension();
```  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathRemoveExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveextensiona)。  
  
##  <a name="removefilespec"></a>  CPathT::RemoveFileSpec  
 如果它們，請呼叫這個方法，以從路徑移除尾端的檔案名稱及反斜線。  
  
```
BOOL RemoveFileSpec();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 TRUE 失敗則為 FALSE。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathRemoveFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovefilespeca)。  
  
##  <a name="renameextension"></a>  CPathT::RenameExtension  
 呼叫這個方法來取代新的延伸模組的路徑中的檔案名稱副檔名。 如果檔案名稱不包含延伸模組，擴充功能就會附加至路徑的結尾。  
  
```
BOOL RenameExtension(PCXSTR pszExtension);
```  
  
### <a name="parameters"></a>參數  
 *pszExtension*  
 新的檔案名稱副檔名，前面加上"。"字元。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回 TRUE 失敗則為 FALSE。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathRenameExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathrenameextensiona)。  
  
##  <a name="skiproot"></a>  CPathT::SkipRoot  
 呼叫這個方法來剖析路徑，將忽略磁碟機代號或 UNC （通用命名慣例） 伺服器/共用路徑的任何部分。  
  
```
int SkipRoot() const;
```  
  
### <a name="return-value"></a>傳回值  
 傳回會遵循 （磁碟機代號或 UNC 伺服器/共用） 的根的子路徑的開頭位置。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathSkipRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathskiproota)。  
  
##  <a name="strippath"></a>  CPathT::StripPath  
 呼叫這個方法來移除完整的路徑和檔案名稱的路徑部分。  
  
```
void StripPath();
```  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathStripPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathstrippatha)。  
  
##  <a name="striptoroot"></a>  CPathT::StripToRoot  
 呼叫這個方法來移除所有的部分，除了根資訊的路徑。  
  
```
BOOL StripToRoot();
```  
  
### <a name="return-value"></a>傳回值  
 如果有效的磁碟機代號，則為 TRUE 的傳回找不到或 FALSE 在路徑中，否則為。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathStripToRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathstriptoroota)。  
  
##  <a name="unquotespaces"></a>  CPathT::UnquoteSpaces  
 呼叫這個方法來移除開頭和結尾的路徑中的引號。  
  
```
void UnquoteSpaces();
```  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [PathUnquoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathunquotespacesa)。  
  
##  <a name="xchar"></a>  CPathT::XCHAR  
 字元類型。  
  
```
typedef StringType::XCHAR XCHAR;
```  
  
### <a name="remarks"></a>備註  
 `StringType` 是範本參數`CPathT`。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../atl/reference/atl-classes.md)   
 [CStringT 類別](../../atl-mfc-shared/reference/cstringt-class.md)