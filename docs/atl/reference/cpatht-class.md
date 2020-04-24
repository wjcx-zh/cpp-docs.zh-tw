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
ms.openlocfilehash: 76273e7fbfa50e610b437e11859821374413d008
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032130"
---
# <a name="cpatht-class"></a>CPathT 類別

此類表示路徑。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <typename StringType>
class CPathT
```

#### <a name="parameters"></a>參數

*StringType*<br/>
用於路徑的 ATL/MFC 字串類(請參閱[CStringT)。](../../atl-mfc-shared/reference/cstringt-class.md)

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|[CPathT::PCXSTR](#pcxstr)|常量字串類型。|
|[CPathT::PXSTR](#pxstr)|string 類型。|
|[CPathT:XCHAR](#xchar)|字元類型。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CPathT:CPathT](#cpatht)|路徑的構造函數。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CPathT::新增反斜杠](#addbackslash)|呼叫此方法向字串的末尾添加反斜杠,以建立路徑的正確語法。|
|[CPathT::新增擴展](#addextension)|呼叫此方法以向路徑添加檔案副檔名。|
|[CPathT::附加](#append)|呼叫此方法以將字串追加到當前路徑。|
|[CPathT::建構根](#buildroot)|調用此方法從給定驅動器號創建根路徑。|
|[CPathT:規範化](#canonicalize)|調用此方法將路徑轉換為規範形式。|
|[CPathT::合併](#combine)|呼叫此方法將表示目錄名稱的字串和表示檔案路徑名稱的字串串聯到一個路徑中。|
|[CPathT::通用首頭](#commonprefix)|呼叫此方法以確定指定的路徑是否與當前路徑共用公共首碼。|
|[CPathT::緊湊路徑](#compactpath)|調用此方法可截取檔路徑,方法是將路徑元件替換為省略號,以適合給定圖元寬度。|
|[CPathT::壓縮路徑](#compactpathex)|呼叫此方法,通過將路徑元件替換為省略號來截取檔路徑以適合給定數量的字元。|
|[CPathT:檔案存在](#fileexists)|呼叫此方法以檢查此路徑名稱下的檔是否存在。|
|[CPathT::尋找擴充](#findextension)|呼叫此方法以查找路徑中檔案副檔名的位置。|
|[CPathT::尋找檔案名](#findfilename)|呼叫此方法以查找檔名在路徑中的位置。|
|[CPathT:抓取磁碟機號碼](#getdrivenumber)|調用此方法以在「A」到「Z」範圍內搜索驅動器號路徑並返回相應的驅動器號。|
|[CPathT:取得延伸](#getextension)|呼叫此方法從路徑獲取檔副檔名。|
|[CPathT:是目錄](#isdirectory)|呼叫此方法以檢查路徑是否為有效目錄。|
|[CPathT:是檔案規格](#isfilespec)|呼叫此方法以搜尋路徑以查找任何路徑分隔字元(例如,":"或'')。\\ 如果不存在路徑分隔字元,則路徑被視為文件規格路徑。|
|[CPathT:isprefix](#isprefix)|呼叫此方法以確定路徑是否包含*pszPrefix*傳遞的類型的有效前置字串。|
|[CPathT:相對](#isrelative)|調用此方法以確定路徑是否相對。|
|[CPathT:是根](#isroot)|呼叫此方法以確定路徑是否為目錄根。|
|[CPathT::IsSameRoot](#issameroot)|呼叫此方法以確定另一個路徑是否具有與當前路徑的通用根元件。|
|[CPathT:ISUNC](#isunc)|呼叫此方法以確定路徑是否是伺服器和共用的有效 UNC(通用命名約定)路徑。|
|[CPathT:isUNCServer](#isuncserver)|呼叫此方法以確定路徑是否僅是伺服器的有效 UNC(通用命名約定)路徑。|
|[CPathT:isUNCServer共用](#isuncservershare)|呼叫此方法以確定路徑是否是有效的 UNC(通用命名約定)共用路徑\\\ 、*伺服器*\ *共用*。|
|[CPathT::製作漂亮](#makepretty)|呼叫此方法可將路徑轉換為所有小寫字元,以使路徑的外觀一致。|
|[CPathT::匹配規格](#matchspec)|呼叫此方法以搜尋包含通配符匹配類型的字串的路徑。|
|[CPathT::報價空間](#quotespaces)|如果路徑包含任何空格,則調用此方法以引弧括上路徑。|
|[CPatht::相對路徑](#relativepathto)|呼叫此方法以建立從一個檔或資料夾到另一個檔案或資料夾的相對路徑。|
|[CPathT::刪除阿格](#removeargs)|呼叫此方法從路徑中刪除任何命令列參數。|
|[CPathT::刪除反斜杠](#removebackslash)|呼叫此方法以從路徑中刪除尾隨反斜杠。|
|[CPathT::刪除空白](#removeblanks)|呼叫此方法從路徑中刪除所有前導空格和尾隨空格。|
|[CPathT::刪除延伸](#removeextension)|呼叫此方法以從路徑中刪除檔案副檔名(如果有)。|
|[CPathT::刪除檔案規格](#removefilespec)|呼叫此方法以從路徑中刪除尾隨檔名和反斜杠(如果有)。|
|[CPathT::重新命名擴充](#renameextension)|呼叫此方法以將路徑中的檔案名副檔名替換為新的副檔名。 如果檔名不包含副檔名,則擴展名將附加到字串的末尾。|
|[CPathT::跳過根](#skiproot)|呼叫此方法以分析路徑,忽略驅動器號或 UNC 伺服器/共用路徑部件。|
|[CPathT::條帶路徑](#strippath)|呼叫此方法以刪除完全限定的路徑和檔名的路徑部分。|
|[CPatht::條紋根](#striptoroot)|呼叫此方法以刪除路徑的所有部分,但根資訊除外。|
|[CPathT:無引號空格](#unquotespaces)|呼叫此方法以從路徑的開頭和結尾刪除引號。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CPathT::運算元 const 字串類型&](#operator_const_stringtype_amp)|此運算子允許將對象視為字串。|
|[CPathT::操作員 CPathT::PCXSTR](#operator_cpatht__pcxstr)|此運算子允許將對象視為字串。|
|[CPathT::運算元字串類型&](#operator_stringtype_amp)|此運算子允許將對象視為字串。|
|[CPathT::操作員 |](#operator_add_eq)|此運算元將字串追加到路徑中。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CPathT:m_strPath](#m_strpath)|路徑。|

## <a name="remarks"></a>備註

`CPath``CPathA`,並且`CPathW`是定義的實例化`CPathT`, 如下所示:

`typedef CPathT< CString > CPath;`

`typedef CPathT< CStringA > CPathA;`

`typedef CPathT< CStringW > CPathW;`

## <a name="requirements"></a>需求

**標題:** atlpath.h

## <a name="cpathtaddbackslash"></a><a name="addbackslash"></a>CPathT::新增反斜杠

呼叫此方法向字串的末尾添加反斜杠,以建立路徑的正確語法。 如果路徑已具有尾隨反斜杠,則不會添加反斜杠。

```cpp
void AddBackslash();
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[路徑新增回斜槓](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw)。

## <a name="cpathtaddextension"></a><a name="addextension"></a>CPathT::新增擴展

呼叫此方法以向路徑添加檔案副檔名。

```
BOOL AddExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>參數

*psz 擴充*<br/>
要添加的檔副檔名。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

有關詳細資訊,請參考[路徑新增擴充](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw)。

## <a name="cpathtappend"></a><a name="append"></a>CPathT::附加

呼叫此方法以將字串追加到當前路徑。

```
BOOL Append(PCXSTR pszMore);
```

### <a name="parameters"></a>參數

*pszMore*<br/>
要附加的字串。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[路徑應用](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw)。

## <a name="cpathtbuildroot"></a><a name="buildroot"></a>CPathT::建構根

調用此方法從給定驅動器號創建根路徑。

```cpp
void BuildRoot(int iDrive);
```

### <a name="parameters"></a>參數

*iDrive*<br/>
驅動器號(0 為 A:,1 表示 B:,等等)。

### <a name="remarks"></a>備註

有關詳細資訊,請參考[路徑建構根](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw)。

## <a name="cpathtcanonicalize"></a><a name="canonicalize"></a>CPathT:規範化

調用此方法將路徑轉換為規範形式。

```cpp
void Canonicalize();
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[路徑化](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew)。

## <a name="cpathtcombine"></a><a name="combine"></a>CPathT::合併

呼叫此方法將表示目錄名稱的字串和表示檔案路徑名稱的字串串聯到一個路徑中。

```cpp
void Combine(PCXSTR pszDir, PCXSTR  pszFile);
```

### <a name="parameters"></a>參數

*皮茲迪爾*<br/>
目錄路徑。

*pszFile*<br/>
檔案路徑。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[路徑合併](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew)。

## <a name="cpathtcommonprefix"></a><a name="commonprefix"></a>CPathT::通用首頭

呼叫此方法以確定指定的路徑是否與當前路徑共用公共首碼。

```
CPathT<StringType> CommonPrefix(PCXSTR pszOther);
```

### <a name="parameters"></a>參數

*pszOther*<br/>
要與當前路徑進行比較的路徑。

### <a name="return-value"></a>傳回值

返回公共首碼。

### <a name="remarks"></a>備註

首碼是以下類型之一:"C:",".",".",".","."."."."."."\\ \\\\\\". 有關詳細資訊,請參閱[路徑公共前置字](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw)串 。

## <a name="cpathtcompactpath"></a><a name="compactpath"></a>CPathT::緊湊路徑

調用此方法可截取檔路徑,方法是將路徑元件替換為省略號,以適合給定圖元寬度。

```
BOOL CompactPath(HDC hDC, UINT nWidth);
```

### <a name="parameters"></a>參數

*hDC*<br/>
用於字體指標的設備上下文。

*n 寬度*<br/>
字串將強制擬合的寬度(以像素為單位)。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

有關詳細資訊,請參考[路徑壓縮路徑](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw)。

## <a name="cpathtcompactpathex"></a><a name="compactpathex"></a>CPathT::壓縮路徑

呼叫此方法,通過將路徑元件替換為省略號來截取檔路徑以適合給定數量的字元。

```
BOOL CompactPathEx(UINT nMaxChars, DWORD dwFlags = 0);
```

### <a name="parameters"></a>參數

*nMaxChars*<br/>
新字串中要包含的最大字元數,包括終止 NULL 字元。

*dwFlags*<br/>
已保留。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[路徑壓縮路徑Ex](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw)。

## <a name="cpathtcpatht"></a><a name="cpatht"></a>CPathT:CPathT

建構函式。

```
CPathT(PCXSTR pszPath);
CPathT(const CPathT<StringType>& path);
CPathT() throw();
```

### <a name="parameters"></a>參數

*pszPath*<br/>
指向路徑字串的指標。

*path*<br/>
路徑字串。

## <a name="cpathtfileexists"></a><a name="fileexists"></a>CPathT:檔案存在

呼叫此方法以檢查此路徑名稱下的檔是否存在。

```
BOOL FileExists() const;
```

### <a name="return-value"></a>傳回值

如果檔存在,則返回 TRUE,否則返回 FALSE。

### <a name="remarks"></a>備註

有關詳細資訊,請參考[路徑檔存在](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw)。

## <a name="cpathtfindextension"></a><a name="findextension"></a>CPathT::尋找擴充

呼叫此方法以查找路徑中檔案副檔名的位置。

```
int FindExtension() const;
```

### <a name="return-value"></a>傳回值

返回延伸之前的" 的位置。 如果未找到擴展,則返回 -1。

### <a name="remarks"></a>備註

有關詳細資訊,請參考[路徑尋找延伸](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw)。

## <a name="cpathtfindfilename"></a><a name="findfilename"></a>CPathT::尋找檔案名

呼叫此方法以查找檔名在路徑中的位置。

```
int FindFileName() const;
```

### <a name="return-value"></a>傳回值

返回檔名的位置。 如果未找到檔名,則返回 -1。

### <a name="remarks"></a>備註

關於詳細資訊,請參考[路徑尋找檔案名稱](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)。

## <a name="cpathtgetdrivenumber"></a><a name="getdrivenumber"></a>CPathT:抓取磁碟機號碼

調用此方法以在「A」到「Z」範圍內搜索驅動器號路徑並返回相應的驅動器號。

```
int GetDriveNumber() const;
```

### <a name="return-value"></a>傳回值

如果路徑具有驅動器號,則將驅動器號作為從 0 到 25 的整數(對應於"A"到"Z")返回,否則為 -1。

### <a name="remarks"></a>備註

關於詳細資訊,請參考[路徑抓取磁碟器編號](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw)。

## <a name="cpathtgetextension"></a><a name="getextension"></a>CPathT:取得延伸

呼叫此方法從路徑獲取檔副檔名。

```
StringType GetExtension() const;
```

### <a name="return-value"></a>傳回值

返回文件副檔名。

## <a name="cpathtisdirectory"></a><a name="isdirectory"></a>CPathT:是目錄

呼叫此方法以檢查路徑是否為有效目錄。

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>傳回值

如果路徑是目錄,則返回非零值 (16),否則為 FALSE。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw)。

## <a name="cpathtisfilespec"></a><a name="isfilespec"></a>CPathT:是檔案規格

呼叫此方法以搜尋路徑以查找任何路徑分隔字元(例如,":"或'')。\\ 如果不存在路徑分隔字元,則路徑被視為文件規格路徑。

```
BOOL IsFileSpec() const;
```

### <a name="return-value"></a>傳回值

如果路徑中沒有路徑分隔字元,則返回 TRUE;如果存在路徑分隔字元,則返回 FALSE。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[PathisFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw)。

## <a name="cpathtisprefix"></a><a name="isprefix"></a>CPathT:isprefix

呼叫此方法以確定路徑是否包含*pszPrefix*傳遞的類型的有效前置字串。

```
BOOL IsPrefix(PCXSTR pszPrefix) const;
```

### <a name="parameters"></a>參數

*pszPrefix*<br/>
要為其搜索的首碼。 首碼是以下類型之一:"C:",".",".",".","."."."."."."\\ \\\\\\".

### <a name="return-value"></a>傳回值

如果路徑包含首碼,則返回 TRUE,否則返回 FALSE。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[路徑前置字](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)串 。

## <a name="cpathtisrelative"></a><a name="isrelative"></a>CPathT:相對

調用此方法以確定路徑是否相對。

```
BOOL IsRelative() const;
```

### <a name="return-value"></a>傳回值

如果路徑是相對的,則返回 TRUE;如果路徑是絕對的,則返回 FALSE。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[路徑相關](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew)。

## <a name="cpathtisroot"></a><a name="isroot"></a>CPathT:是根

呼叫此方法以確定路徑是否為目錄根。

```
BOOL IsRoot() const;
```

### <a name="return-value"></a>傳回值

如果路徑是根,則返回 TRUE,否則返回 FALSE。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[PathIsroot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw)。

## <a name="cpathtissameroot"></a><a name="issameroot"></a>CPathT::IsSameRoot

呼叫此方法以確定另一個路徑是否具有與當前路徑的通用根元件。

```
BOOL IsSameRoot(PCXSTR pszOther) const;
```

### <a name="parameters"></a>參數

*pszOther*<br/>
另一條路徑。

### <a name="return-value"></a>傳回值

如果兩個字串具有相同的根元件,則返回 TRUE,否則返回 FALSE。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[路徑IsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw)。

## <a name="cpathtisunc"></a><a name="isunc"></a>CPathT:ISUNC

呼叫此方法以確定路徑是否是伺服器和共用的有效 UNC(通用命名約定)路徑。

```
BOOL IsUNC() const;
```

### <a name="return-value"></a>傳回值

如果路徑是有效的 UNC 路徑,則返回 TRUE,否則返回 FALSE。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[PathisUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw)。

## <a name="cpathtisuncserver"></a><a name="isuncserver"></a>CPathT:isUNCServer

呼叫此方法以確定路徑是否僅是伺服器的有效 UNC(通用命名約定)路徑。

```
BOOL IsUNCServer() const;
```

### <a name="return-value"></a>傳回值

如果字串僅針對伺服器(無共用名稱)或 FALSE 為「FALSE」,則返回 TRUE。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[PathisUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw)。

## <a name="cpathtisuncservershare"></a><a name="isuncservershare"></a>CPathT:isUNCServer共用

呼叫此方法以確定路徑是否是有效的 UNC(通用命名約定)共用路徑\\\ 、*伺服器*\ *共用*。

```
BOOL IsUNCServerShare() const;
```

### <a name="return-value"></a>傳回值

如果路徑\\\ *位於伺服器*\ *共用*窗體中,則返回 TRUE,否則返回 FALSE。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[PathisUNCServer 共用](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew)。

## <a name="cpathtm_strpath"></a><a name="m_strpath"></a>CPathT:m_strPath

路徑。

```
StringType m_strPath;
```

### <a name="remarks"></a>備註

`StringType`是的`CPathT`範本參數。

## <a name="cpathtmakepretty"></a><a name="makepretty"></a>CPathT::製作漂亮

呼叫此方法可將路徑轉換為所有小寫字元,以使路徑的外觀一致。

```
BOOL MakePretty();
```

### <a name="return-value"></a>傳回值

如果路徑已轉換,則返回 TRUE,否則返回 FALSE。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[PathMake"美麗](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw)"。

## <a name="cpathtmatchspec"></a><a name="matchspec"></a>CPathT::匹配規格

呼叫此方法以搜尋包含通配符匹配類型的字串的路徑。

```
BOOL MatchSpec(PCXSTR pszSpec) const;
```

### <a name="parameters"></a>參數

*pszSpec*<br/>
指向具有要搜尋的檔案類型的 null 終止字串的指標。 例如,要測試當前路徑上的檔是否是 DOC 檔,應將*pszSpec*設置為"*.doc"。

### <a name="return-value"></a>傳回值

如果字串匹配,則返回 TRUE,否則返回 FALSE。

### <a name="remarks"></a>備註

有關詳細資訊,請參考[路徑符合 Spec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw)。

## <a name="cpathtoperator-"></a><a name="operator_add_eq"></a>CPathT::操作員 |

此運算元將字串追加到路徑中。

```
CPathT<StringType>& operator+=(PCXSTR pszMore);
```

### <a name="parameters"></a>參數

*pszMore*<br/>
要附加的字串。

### <a name="return-value"></a>傳回值

返回更新的路徑。

## <a name="cpathtoperator-const-stringtype-amp"></a><a name="operator_const_stringtype_amp"></a>CPathT::運算元 const 字串類型&amp;

此運算子允許將對象視為字串。

```
operator const StringType&() const throw();
```

### <a name="return-value"></a>傳回值

傳回表示此物件管理的當前路徑的字串。

## <a name="cpathtoperator-cpathtpcxstr"></a><a name="operator_cpatht__pcxstr"></a>CPathT::操作員 CPathT::PCXSTR

此運算子允許將對象視為字串。

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>傳回值

傳回表示此物件管理的當前路徑的字串。

## <a name="cpathtoperator-stringtype-amp"></a><a name="operator_stringtype_amp"></a>CPathT::運算元字串類型&amp;

此運算子允許將對象視為字串。

```
operator StringType&() throw();
```

### <a name="return-value"></a>傳回值

傳回表示此物件管理的當前路徑的字串。

## <a name="cpathtpcxstr"></a><a name="pcxstr"></a>CPathT::PCXSTR

常量字串類型。

```
typedef StringType::PCXSTR PCXSTR;
```

### <a name="remarks"></a>備註

`StringType`是的`CPathT`範本參數。

## <a name="cpathtpxstr"></a><a name="pxstr"></a>CPathT::PXSTR

string 類型。

```
typedef StringType::PXSTR PXSTR;
```

### <a name="remarks"></a>備註

`StringType`是的`CPathT`範本參數。

## <a name="cpathtquotespaces"></a><a name="quotespaces"></a>CPathT::報價空間

如果路徑包含任何空格,則調用此方法以引弧括上路徑。

```cpp
void QuoteSpaces();
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[路徑報價空間](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw)。

## <a name="cpathtrelativepathto"></a><a name="relativepathto"></a>CPatht::相對路徑

呼叫此方法以建立從一個檔或資料夾到另一個檔案或資料夾的相對路徑。

```
BOOL RelativePathTo(
    PCXSTR pszFrom,
    DWORD dwAttrFrom,
    PCXSTR pszTo,
    DWORD dwAttrTo);
```

### <a name="parameters"></a>參數

*psz 從*<br/>
相對路徑的開頭。

*dwAttr 從*<br/>
*pszfrom*的文件屬性。 如果此值包含FILE_ATTRIBUTE_DIRECTORY,則*pszFrom*假定為目錄;如果此值包含 FILE_ATTRIBUTE_DIRECTORY,則 pszFrom 假定為目錄。否則 *,pszFrom*假定為檔。

*pszto*<br/>
相對路徑的終點。

*德沃特爾托*<br/>
*pszTo*的文件屬性。 如果此值包含FILE_ATTRIBUTE_DIRECTORY,則*pszTo*假定為目錄;如果此值包含 FILE_ATTRIBUTE_DIRECTORY,則 pszTo 假定為目錄。否則 *,pszTo*假定為檔。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[路徑相對路徑。](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow)

## <a name="cpathtremoveargs"></a><a name="removeargs"></a>CPathT::刪除阿格

呼叫此方法從路徑中刪除任何命令列參數。

```cpp
void RemoveArgs();
```

### <a name="remarks"></a>備註

有關詳細資訊,請參考[路徑刪除 。](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw)

## <a name="cpathtremovebackslash"></a><a name="removebackslash"></a>CPathT::刪除反斜杠

呼叫此方法以從路徑中刪除尾隨反斜杠。

```cpp
void RemoveBackslash();
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[路徑刪除反斜槓](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw)。

## <a name="cpathtremoveblanks"></a><a name="removeblanks"></a>CPathT::刪除空白

呼叫此方法從路徑中刪除所有前導空格和尾隨空格。

```cpp
void RemoveBlanks();
```

### <a name="remarks"></a>備註

有關詳細資訊,請參考[空白](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw)。

## <a name="cpathtremoveextension"></a><a name="removeextension"></a>CPathT::刪除延伸

呼叫此方法以從路徑中刪除檔案副檔名(如果有)。

```cpp
void RemoveExtension();
```

### <a name="remarks"></a>備註

有關詳細資訊,請參考[副檔](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw)。

## <a name="cpathtremovefilespec"></a><a name="removefilespec"></a>CPathT::刪除檔案規格

呼叫此方法以從路徑中刪除尾隨檔名和反斜杠(如果有)。

```
BOOL RemoveFileSpec();
```

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

關於詳細資訊,請參考[檔案Spec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw)。

## <a name="cpathtrenameextension"></a><a name="renameextension"></a>CPathT::重新命名擴充

呼叫此方法以將路徑中的檔案名副檔名替換為新的副檔名。 如果檔名不包含副檔名,則擴展名將附加到路徑的末尾。

```
BOOL RenameExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>參數

*psz 擴充*<br/>
新的檔案名副檔名,前面有一個"."字元。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

有關詳細資訊,請參考[路徑重新命名延伸](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw)。

## <a name="cpathtskiproot"></a><a name="skiproot"></a>CPathT::跳過根

呼叫此方法以分析路徑,忽略驅動器號或 UNC(通用命名約定)伺服器/共用路徑部件。

```
int SkipRoot() const;
```

### <a name="return-value"></a>傳回值

返回根(驅動器號或 UNC 伺服器/共用)後面的子路徑的開頭的位置。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[路徑跳過根](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw)。

## <a name="cpathtstrippath"></a><a name="strippath"></a>CPathT::條帶路徑

呼叫此方法以刪除完全限定的路徑和檔名的路徑部分。

```cpp
void StripPath();
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[路徑條帶路徑](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw)。

## <a name="cpathtstriptoroot"></a><a name="striptoroot"></a>CPatht::條紋根

呼叫此方法以刪除路徑的所有部分,但根資訊除外。

```
BOOL StripToRoot();
```

### <a name="return-value"></a>傳回值

如果在路徑中找到有效的驅動器號,則返回 TRUE,否則返回 FALSE。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱[路徑條塊](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw)。

## <a name="cpathtunquotespaces"></a><a name="unquotespaces"></a>CPathT:無引號空格

呼叫此方法以從路徑的開頭和結尾刪除引號。

```cpp
void UnquoteSpaces();
```

### <a name="remarks"></a>備註

關於詳細資訊,請參考[路徑取消參考空白](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw)。

## <a name="cpathtxchar"></a><a name="xchar"></a>CPathT:XCHAR

字元類型。

```
typedef StringType::XCHAR XCHAR;
```

### <a name="remarks"></a>備註

`StringType`是的`CPathT`範本參數。

## <a name="see-also"></a>另請參閱

[類別](../../atl/reference/atl-classes.md)<br/>
[CStringT 類別](../../atl-mfc-shared/reference/cstringt-class.md)
