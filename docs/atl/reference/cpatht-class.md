---
title: CPathT 類別
ms.date: 03/27/2019
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
helpviewer_keywords:
- CPathT class
ms.assetid: eba4137d-1fd2-4b44-a2e1-0944db64df3c
ms.openlocfilehash: ba1c831d772deef34449d17adc2c8e7a6f90eaef
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "69496623"
---
# <a name="cpatht-class"></a>CPathT 類別

此類別代表路徑。

> [!IMPORTANT]
> 這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <typename StringType>
class CPathT
```

#### <a name="parameters"></a>參數

*StringType*<br/>
要用於路徑的 ATL/MFC 字串類別（請參閱[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)）。

## <a name="members"></a>Members

### <a name="public-typedefs"></a>公用 Typedefs

|[屬性]|描述|
|----------|-----------------|
|[CPathT：:P CXSTR](#pcxstr)|常數位串類型。|
|[CPathT：:P XSTR](#pxstr)|字串類型。|
|[CPathT::XCHAR](#xchar)|字元類型。|

### <a name="public-constructors"></a>公用建構函式

|[屬性]|描述|
|----------|-----------------|
|[CPathT::CPathT](#cpatht)|路徑的構造函式。|

### <a name="public-methods"></a>公用方法

|[屬性]|描述|
|----------|-----------------|
|[CPathT::AddBackslash](#addbackslash)|呼叫這個方法，在字串結尾加上反斜線，以建立路徑的正確語法。|
|[CPathT::AddExtension](#addextension)|呼叫這個方法，將副檔名新增至路徑。|
|[CPathT：： Append](#append)|呼叫這個方法，將字串附加至目前的路徑。|
|[CPathT：： BuildRoot](#buildroot)|呼叫此方法，以從指定的磁片磁碟機編號建立根路徑。|
|[CPathT：：正常化](#canonicalize)|呼叫這個方法，將路徑轉換成標準格式。|
|[CPathT：：組合](#combine)|呼叫這個方法，將代表目錄名稱的字串，以及代表檔案路徑名稱的字串串連成一個路徑。|
|[CPathT::CommonPrefix](#commonprefix)|呼叫這個方法，以判斷指定的路徑是否與目前的路徑共用一般前置詞。|
|[CPathT::CompactPath](#compactpath)|呼叫這個方法，藉由以省略號取代路徑元件，以截斷檔案路徑以符合指定的圖元寬度。|
|[CPathT::CompactPathEx](#compactpathex)|呼叫這個方法來截斷檔案路徑，使其符合指定的字元數，方法是以省略號取代路徑元件。|
|[CPathT：： FileExists](#fileexists)|呼叫這個方法，以檢查此路徑名稱的檔案是否存在。|
|[CPathT::FindExtension](#findextension)|呼叫這個方法，以在路徑中尋找副檔名的位置。|
|[CPathT::FindFileName](#findfilename)|呼叫這個方法，以尋找路徑中檔案名的位置。|
|[CPathT::GetDriveNumber](#getdrivenumber)|呼叫此方法，以在路徑 ' A ' 到 ' Z ' 的範圍內搜尋磁碟機號，並傳回對應的磁片磁碟機編號。|
|[CPathT::GetExtension](#getextension)|呼叫這個方法，以從路徑取得副檔名。|
|[CPathT::IsDirectory](#isdirectory)|呼叫這個方法，以檢查路徑是否為有效的目錄。|
|[CPathT::IsFileSpec](#isfilespec)|呼叫這個方法，以搜尋路徑是否有任何路徑分隔字元（例如 '： ' 或 ' \\ '）。 如果沒有任何路徑分隔字元存在，則會將路徑視為檔案規格路徑。|
|[CPathT::IsPrefix](#isprefix)|呼叫這個方法，以判斷路徑是否包含*pszPrefix*所傳遞之類型的有效前置詞。|
|[CPathT::IsRelative](#isrelative)|呼叫這個方法，以判斷路徑是否為相對路徑。|
|[CPathT::IsRoot](#isroot)|呼叫這個方法，以判斷路徑是否為目錄根目錄。|
|[CPathT::IsSameRoot](#issameroot)|呼叫這個方法，以判斷另一個路徑是否有具有目前路徑的通用根元件。|
|[CPathT::IsUNC](#isunc)|呼叫這個方法，以判斷路徑是否為伺服器和共用的有效 UNC （通用命名慣例）路徑。|
|[CPathT::IsUNCServer](#isuncserver)|呼叫這個方法，以判斷路徑是否僅適用于伺服器的有效 UNC （通用命名慣例）路徑。|
|[CPathT::IsUNCServerShare](#isuncservershare)|呼叫這個方法，以判斷路徑是否為有效的 UNC （通用命名慣例）共用路徑，\\ \ *伺服器*\ *共用*。|
|[CPathT::MakePretty](#makepretty)|呼叫此方法可將路徑轉換成所有小寫字元，讓路徑具有一致的外觀。|
|[CPathT::MatchSpec](#matchspec)|呼叫這個方法來搜尋包含萬用字元比對類型之字串的路徑。|
|[CPathT::QuoteSpaces](#quotespaces)|呼叫這個方法，以引號括住路徑（如果它包含任何空格）。|
|[CPathT::RelativePathTo](#relativepathto)|呼叫這個方法，以建立一個檔案或資料夾到另一個的相對路徑。|
|[CPathT::RemoveArgs](#removeargs)|呼叫這個方法，從路徑移除任何命令列引數。|
|[CPathT::RemoveBackslash](#removebackslash)|呼叫這個方法，從路徑移除尾端反斜線。|
|[CPathT::RemoveBlanks](#removeblanks)|呼叫這個方法，從路徑移除所有開頭和尾端空格。|
|[CPathT::RemoveExtension](#removeextension)|呼叫此方法可從路徑中移除副檔名（如果有的話）。|
|[CPathT::RemoveFileSpec](#removefilespec)|呼叫這個方法，從路徑移除尾端的檔案名和反斜線（如果有的話）。|
|[CPathT::RenameExtension](#renameextension)|呼叫這個方法，以新的副檔名取代路徑中的副檔名。 如果檔案名不包含副檔名，延伸模組就會附加至字串的結尾。|
|[CPathT::SkipRoot](#skiproot)|呼叫這個方法來剖析路徑，忽略磁碟機號或 UNC 伺服器/共用路徑部分。|
|[CPathT::StripPath](#strippath)|呼叫這個方法，以移除完整路徑和檔案名的路徑部分。|
|[CPathT::StripToRoot](#striptoroot)|呼叫此方法可移除路徑的所有部分，但不包括根資訊。|
|[CPathT::UnquoteSpaces](#unquotespaces)|呼叫這個方法，從路徑的開頭和結尾移除引號。|

### <a name="public-operators"></a>公用運算子

|[屬性]|描述|
|----------|-----------------|
|[CPathT：： operator const StringType &](#operator_const_stringtype_amp)|這個運算子可讓物件的處理方式與字串相同。|
|[CPathT：： operator CPathT：:P CXSTR](#operator_cpatht__pcxstr)|這個運算子可讓物件的處理方式與字串相同。|
|[CPathT：： operator StringType &](#operator_stringtype_amp)|這個運算子可讓物件的處理方式與字串相同。|
|[CPathT：： operator + =](#operator_add_eq)|這個運算子會將字串附加至路徑。|

### <a name="public-data-members"></a>公用資料成員

|[屬性]|描述|
|----------|-----------------|
|[CPathT::m_strPath](#m_strpath)|路徑。|

## <a name="remarks"></a>備註

`CPath`、`CPathA` 和 `CPathW` 是定義的 `CPathT` 具現化，如下所示：

`typedef CPathT< CString > CPath;`

`typedef CPathT< CStringA > CPathA;`

`typedef CPathT< CStringW > CPathW;`

## <a name="requirements"></a>需求

**標頭：** 與 atlpath.h。h

##  <a name="addbackslash"></a>CPathT::AddBackslash

呼叫這個方法，在字串結尾加上反斜線，以建立路徑的正確語法。 如果路徑中已有尾端的反斜線，則不會新增反斜線。

```
void AddBackslash();
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathaddbackslash 式](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw)。

##  <a name="addextension"></a>CPathT::AddExtension

呼叫這個方法，將副檔名新增至路徑。

```
BOOL AddExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>參數

*pszExtension*<br/>
要加入的副檔名。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathaddextension 式](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw)。

##  <a name="append"></a>CPathT：： Append

呼叫這個方法，將字串附加至目前的路徑。

```
BOOL Append(PCXSTR pszMore);
```

### <a name="parameters"></a>參數

*pszMore*<br/>
要附加的字串。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathappend 式](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw)。

##  <a name="buildroot"></a>CPathT：： BuildRoot

呼叫此方法，以從指定的磁片磁碟機編號建立根路徑。

```
void BuildRoot(int iDrive);
```

### <a name="parameters"></a>參數

*iDrive*<br/>
磁片磁碟機編號（0是：，1是 B：，依此類推）。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathbuildroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw)。

##  <a name="canonicalize"></a>CPathT：：正常化

呼叫這個方法，將路徑轉換成標準格式。

```
void Canonicalize();
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathcanonicalize 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew)。

##  <a name="combine"></a>CPathT：：組合

呼叫這個方法，將代表目錄名稱的字串，以及代表檔案路徑名稱的字串串連成一個路徑。

```
void Combine(PCXSTR pszDir, PCXSTR  pszFile);
```

### <a name="parameters"></a>參數

*pszDir*<br/>
目錄路徑。

*pszFile*<br/>
檔案路徑。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathcombine 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew)。

##  <a name="commonprefix"></a>CPathT::CommonPrefix

呼叫這個方法，以判斷指定的路徑是否與目前的路徑共用一般前置詞。

```
CPathT<StringType> CommonPrefix(PCXSTR pszOther);
```

### <a name="parameters"></a>參數

*pszOther*<br/>
要與目前物件比較的路徑。

### <a name="return-value"></a>傳回值

傳回一般前置詞。

### <a name="remarks"></a>備註

前置詞是下列其中一種類型： "C： \\ \\"，"."，"..."，"。\\ \\」。 如需詳細資訊，請參閱[pathcommonprefix 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw)。

##  <a name="compactpath"></a>CPathT::CompactPath

呼叫這個方法，藉由以省略號取代路徑元件，以截斷檔案路徑以符合指定的圖元寬度。

```
BOOL CompactPath(HDC hDC, UINT nWidth);
```

### <a name="parameters"></a>參數

*hDC*<br/>
用於字型計量的裝置內容。

*nWidth*<br/>
字串將強制納入的寬度（以圖元為單位）。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathcompactpath 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw)。

##  <a name="compactpathex"></a>CPathT::CompactPathEx

呼叫這個方法來截斷檔案路徑，使其符合指定的字元數，方法是以省略號取代路徑元件。

```
BOOL CompactPathEx(UINT nMaxChars, DWORD dwFlags = 0);
```

### <a name="parameters"></a>參數

*nMaxChars*<br/>
要包含在新字串中的最大字元數，包括終止的 Null 字元。

*dwFlags*<br/>
保留的。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathcompactpathex 式](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw)。

##  <a name="cpatht"></a>CPathT::CPathT

建構函式。

```
CPathT(PCXSTR pszPath);
CPathT(const CPathT<StringType>& path);
CPathT() throw();
```

### <a name="parameters"></a>參數

*pszPath*<br/>
路徑字串的指標。

*path*<br/>
路徑字串。

##  <a name="fileexists"></a>CPathT：： FileExists

呼叫這個方法，以檢查此路徑名稱的檔案是否存在。

```
BOOL FileExists() const;
```

### <a name="return-value"></a>傳回值

如果檔案存在，則傳回 TRUE，否則傳回 FALSE。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathfileexists 式](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw)。

##  <a name="findextension"></a>CPathT::FindExtension

呼叫這個方法，以在路徑中尋找副檔名的位置。

```
int FindExtension() const;
```

### <a name="return-value"></a>傳回值

傳回 "." 在擴充功能前面的位置。 如果找不到任何延伸模組，則會傳回-1。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathfindextension 式](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw)。

##  <a name="findfilename"></a>CPathT::FindFileName

呼叫這個方法，以尋找路徑中檔案名的位置。

```
int FindFileName() const;
```

### <a name="return-value"></a>傳回值

傳回檔案名的位置。 如果找不到任何檔案名，則會傳回-1。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathfindfilename 式](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)。

##  <a name="getdrivenumber"></a>CPathT::GetDriveNumber

呼叫此方法，以在路徑 ' A ' 到 ' Z ' 的範圍內搜尋磁碟機號，並傳回對應的磁片磁碟機編號。

```
int GetDriveNumber() const;
```

### <a name="return-value"></a>傳回值

如果路徑具有磁碟機號，則以從0到25的整數（對應至 ' A ' 到 ' Z '）傳回磁片磁碟機編號，否則傳回-1。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathgetdrivenumber 式](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw)。

##  <a name="getextension"></a>CPathT::GetExtension

呼叫這個方法，以從路徑取得副檔名。

```
StringType GetExtension() const;
```

### <a name="return-value"></a>傳回值

傳回副檔名。

##  <a name="isdirectory"></a>CPathT::IsDirectory

呼叫這個方法，以檢查路徑是否為有效的目錄。

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>傳回值

如果路徑是目錄，則傳回非零值（16），否則傳回 FALSE。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathisdirectory 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw)。

##  <a name="isfilespec"></a>CPathT::IsFileSpec

呼叫這個方法，以搜尋路徑是否有任何路徑分隔字元（例如 '： ' 或 ' \\ '）。 如果沒有任何路徑分隔字元存在，則會將路徑視為檔案規格路徑。

```
BOOL IsFileSpec() const;
```

### <a name="return-value"></a>傳回值

如果路徑中沒有路徑分隔字元，則傳回 TRUE; 如果有路徑分隔字元，則傳回 FALSE。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathisfilespec 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw)。

##  <a name="isprefix"></a>CPathT::IsPrefix

呼叫這個方法，以判斷路徑是否包含*pszPrefix*所傳遞之類型的有效前置詞。

```
BOOL IsPrefix(PCXSTR pszPrefix) const;
```

### <a name="parameters"></a>參數

*pszPrefix*<br/>
要搜尋的前置詞。 前置詞是下列其中一種類型： "C： \\ \\"，"."，"..."，"。\\ \\」。

### <a name="return-value"></a>傳回值

如果路徑包含前置詞，則傳回 TRUE，否則傳回 FALSE。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathisprefix 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)。

##  <a name="isrelative"></a>CPathT::IsRelative

呼叫這個方法，以判斷路徑是否為相對路徑。

```
BOOL IsRelative() const;
```

### <a name="return-value"></a>傳回值

如果路徑是相對的，則傳回 TRUE，如果是絕對值，則傳回 FALSE。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathisrelative 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew)。

##  <a name="isroot"></a>CPathT::IsRoot

呼叫這個方法，以判斷路徑是否為目錄根目錄。

```
BOOL IsRoot() const;
```

### <a name="return-value"></a>傳回值

如果路徑是根，則傳回 TRUE，否則傳回 FALSE。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathisroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw)。

##  <a name="issameroot"></a>CPathT::IsSameRoot

呼叫這個方法，以判斷另一個路徑是否有具有目前路徑的通用根元件。

```
BOOL IsSameRoot(PCXSTR pszOther) const;
```

### <a name="parameters"></a>參數

*pszOther*<br/>
另一個路徑。

### <a name="return-value"></a>傳回值

如果兩個字串具有相同的根元件，則傳回 TRUE，否則傳回 FALSE。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathissameroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw)。

##  <a name="isunc"></a>CPathT::IsUNC

呼叫這個方法，以判斷路徑是否為伺服器和共用的有效 UNC （通用命名慣例）路徑。

```
BOOL IsUNC() const;
```

### <a name="return-value"></a>傳回值

如果路徑是有效的 UNC 路徑，則傳回 TRUE，否則傳回 FALSE。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathisunc 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw)。

##  <a name="isuncserver"></a>CPathT::IsUNCServer

呼叫這個方法，以判斷路徑是否僅適用于伺服器的有效 UNC （通用命名慣例）路徑。

```
BOOL IsUNCServer() const;
```

### <a name="return-value"></a>傳回值

如果字串只是伺服器的有效 UNC 路徑（沒有共用名稱），則傳回 TRUE，否則傳回 FALSE。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathisuncserver 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw)。

##  <a name="isuncservershare"></a>CPathT::IsUNCServerShare

呼叫這個方法，以判斷路徑是否為有效的 UNC （通用命名慣例）共用路徑，\\ \ *伺服器*\ *共用*。

```
BOOL IsUNCServerShare() const;
```

### <a name="return-value"></a>傳回值

如果路徑的格式為 \\ \ *server* \ *共用*，則傳回 TRUE，否則傳回 FALSE。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathisuncservershare 式](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew)。

##  <a name="m_strpath"></a>CPathT::m_strPath

路徑。

```
StringType m_strPath;
```

### <a name="remarks"></a>備註

`StringType` 是要 `CPathT` 的範本參數。

##  <a name="makepretty"></a>CPathT::MakePretty

呼叫此方法可將路徑轉換成所有小寫字元，讓路徑具有一致的外觀。

```
BOOL MakePretty();
```

### <a name="return-value"></a>傳回值

如果路徑已轉換，則傳回 TRUE，否則傳回 FALSE。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathmakepretty 式](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw)。

##  <a name="matchspec"></a>CPathT::MatchSpec

呼叫這個方法來搜尋包含萬用字元比對類型之字串的路徑。

```
BOOL MatchSpec(PCXSTR pszSpec) const;
```

### <a name="parameters"></a>參數

*pszSpec*<br/>
以 null 結束的字串指標，其中包含要搜尋的檔案類型。 例如，若要測試位於目前路徑的檔案是否為檔檔， *pszSpec*應該設定為 "* .doc"。

### <a name="return-value"></a>傳回值

如果字串相符，則傳回 TRUE，否則傳回 FALSE。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathmatchspec 式](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw)。

##  <a name="operator_add_eq"></a>CPathT：： operator + =

這個運算子會將字串附加至路徑。

```
CPathT<StringType>& operator+=(PCXSTR pszMore);
```

### <a name="parameters"></a>參數

*pszMore*<br/>
要附加的字串。

### <a name="return-value"></a>傳回值

傳回已更新的路徑。

##  <a name="operator_const_stringtype_amp"></a>CPathT：： operator const StringType &amp;

這個運算子可讓物件的處理方式與字串相同。

```
operator const StringType&() const throw();
```

### <a name="return-value"></a>傳回值

傳回字串，代表這個物件所管理的目前路徑。

##  <a name="operator_cpatht__pcxstr"></a>CPathT：： operator CPathT：:P CXSTR

這個運算子可讓物件的處理方式與字串相同。

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>傳回值

傳回字串，代表這個物件所管理的目前路徑。

##  <a name="operator_stringtype_amp"></a>CPathT：： operator StringType &amp;

這個運算子可讓物件的處理方式與字串相同。

```
operator StringType&() throw();
```

### <a name="return-value"></a>傳回值

傳回字串，代表這個物件所管理的目前路徑。

##  <a name="pcxstr"></a>CPathT：:P CXSTR

常數位串類型。

```
typedef StringType::PCXSTR PCXSTR;
```

### <a name="remarks"></a>備註

`StringType` 是要 `CPathT` 的範本參數。

##  <a name="pxstr"></a>CPathT：:P XSTR

字串類型。

```
typedef StringType::PXSTR PXSTR;
```

### <a name="remarks"></a>備註

`StringType` 是要 `CPathT` 的範本參數。

##  <a name="quotespaces"></a>CPathT::QuoteSpaces

呼叫這個方法，以引號括住路徑（如果它包含任何空格）。

```
void QuoteSpaces();
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathquotespaces 式](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw)。

##  <a name="relativepathto"></a>CPathT::RelativePathTo

呼叫這個方法，以建立一個檔案或資料夾到另一個的相對路徑。

```
BOOL RelativePathTo(
    PCXSTR pszFrom,
    DWORD dwAttrFrom,
    PCXSTR pszTo,
    DWORD dwAttrTo);
```

### <a name="parameters"></a>參數

*pszFrom*<br/>
相對路徑的開頭。

*dwAttrFrom*<br/>
*PszFrom*的檔案屬性。 如果此值包含 FILE_ATTRIBUTE_DIRECTORY，則會假設*pszFrom*為目錄;否則， *pszFrom*會假設為檔案。

*pszTo*<br/>
相對路徑的結束點。

*dwAttrTo*<br/>
*PszTo*的檔案屬性。 如果此值包含 FILE_ATTRIBUTE_DIRECTORY，則會假設*pszTo*為目錄;否則， *pszTo*會假設為檔案。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathrelativepathto 式](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow)。

##  <a name="removeargs"></a>CPathT::RemoveArgs

呼叫這個方法，從路徑移除任何命令列引數。

```
void RemoveArgs();
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathremoveargs 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw)。

##  <a name="removebackslash"></a>CPathT::RemoveBackslash

呼叫這個方法，從路徑移除尾端反斜線。

```
void RemoveBackslash();
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathremovebackslash 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw)。

##  <a name="removeblanks"></a>CPathT::RemoveBlanks

呼叫這個方法，從路徑移除所有開頭和尾端空格。

```
void RemoveBlanks();
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathremoveblanks 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw)。

##  <a name="removeextension"></a>CPathT::RemoveExtension

呼叫此方法可從路徑中移除副檔名（如果有的話）。

```
void RemoveExtension();
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathremoveextension 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw)。

##  <a name="removefilespec"></a>CPathT::RemoveFileSpec

呼叫這個方法，從路徑移除尾端的檔案名和反斜線（如果有的話）。

```
BOOL RemoveFileSpec();
```

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathremovefilespec 式](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw)。

##  <a name="renameextension"></a>CPathT::RenameExtension

呼叫這個方法，以新的副檔名取代路徑中的副檔名。 如果檔案名不包含副檔名，延伸模組就會附加至路徑的結尾。

```
BOOL RenameExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>參數

*pszExtension*<br/>
新的副檔名，前面加上 "." 字元。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathrenameextension 式](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw)。

##  <a name="skiproot"></a>CPathT::SkipRoot

呼叫這個方法來剖析路徑，忽略磁碟機號或 UNC （通用命名慣例）伺服器/共用路徑部分。

```
int SkipRoot() const;
```

### <a name="return-value"></a>傳回值

傳回跟在根（磁碟機號或 UNC 伺服器/共用）後面的子路徑開頭的位置。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathskiproot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw)。

##  <a name="strippath"></a>CPathT::StripPath

呼叫這個方法，以移除完整路徑和檔案名的路徑部分。

```
void StripPath();
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathstrippath 式](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw)。

##  <a name="striptoroot"></a>CPathT::StripToRoot

呼叫此方法可移除路徑的所有部分，但不包括根資訊。

```
BOOL StripToRoot();
```

### <a name="return-value"></a>傳回值

如果在路徑中找到有效的磁碟機號，則傳回 TRUE，否則傳回 FALSE。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathstriptoroot 式](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw)。

##  <a name="unquotespaces"></a>CPathT::UnquoteSpaces

呼叫這個方法，從路徑的開頭和結尾移除引號。

```
void UnquoteSpaces();
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[pathunquotespaces 式](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw)。

##  <a name="xchar"></a>CPathT::XCHAR

字元類型。

```
typedef StringType::XCHAR XCHAR;
```

### <a name="remarks"></a>備註

`StringType` 是要 `CPathT` 的範本參數。

## <a name="see-also"></a>請參閱

[類別](../../atl/reference/atl-classes.md)<br/>
[CStringT 類別](../../atl-mfc-shared/reference/cstringt-class.md)
