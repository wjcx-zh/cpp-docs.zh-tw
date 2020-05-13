---
title: CGopherLocator 類別
ms.date: 11/04/2016
f1_keywords:
- CGopherLocator
- AFXINET/CGopherLocator
- AFXINET/CGopherLocator::CGopherLocator
- AFXINET/CGopherLocator::GetLocatorType
helpviewer_keywords:
- CGopherLocator [MFC], CGopherLocator
- CGopherLocator [MFC], GetLocatorType
ms.assetid: 6fcc015f-5ae6-4959-b936-858634c71019
ms.openlocfilehash: d23ef3dad68c62e74ec64454953ca372b8c31114
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373672"
---
# <a name="cgopherlocator-class"></a>CGopherLocator 類別

從 gopher 伺服器獲取 gopher"定位器",確定定位器的類型,並使定位器可供[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)使用。

> [!NOTE]
> 類`CGopherConnection``CGopherFile` `CGopherFileFind`、`CGopherLocator`、 及其成員已被棄用,因為它們在 Windows XP 平臺上不工作,但它們將繼續在較早的平臺上工作。

## <a name="syntax"></a>語法

```
class CGopherLocator : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CGopher定位器::CGopher定位器](#cgopherlocator)|建構 `CGopherLocator` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CGopher定位器::取得定位器類型](#getlocatortype)|解析 gopher 定位器並確定其屬性。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CGopher定位器::操作員LPCTSTR](#operator_lpctstr)|直接存取為 C`CGopherLocator`樣式 字串儲存在物件中的字元。|

## <a name="remarks"></a>備註

應用程式必須先獲取 gopher 伺服器的定位器,然後才能從該伺服器檢索資訊。 一旦它具有定位器,它必須將定位器視為不透明標記。

每個 gopher 定位器都有確定找到的檔案或伺服器類型的屬性。 有關 gopher 定位器類型的清單,請參閱[GetLocatorType。](#getlocatortype)

應用程式通常使用定位器調用[CGopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile)檢索特定資訊。

要瞭解有關如何`CGopherLocator`與其他 MFC Internet 類合作,請參閱[WinInet](../../mfc/win32-internet-extensions-wininet.md)的 Internet 程式設計文章。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CGopherLocator`

## <a name="requirements"></a>需求

**標題:** afxinet.h

## <a name="cgopherlocatorcgopherlocator"></a><a name="cgopherlocator"></a>CGopher定位器::CGopher定位器

呼叫此成員函式以建立物件`CGopherLocator`。

```
CGopherLocator(const CGopherLocator& ref);
```

### <a name="parameters"></a>參數

*ref*<br/>
對常量`CGopherLocator`物件的引用。

### <a name="remarks"></a>備註

您從不直接創建`CGopherLocator`物件。 相反,調用[CGopherConnection::創建定位器](../../mfc/reference/cgopherconnection-class.md#createlocator)以創建並`CGopherLocator`返回指向 物件的指標。

## <a name="cgopherlocatorgetlocatortype"></a><a name="getlocatortype"></a>CGopher定位器::取得定位器類型

調用此成員函數獲取定位器類型。

```
BOOL GetLocatorType(DWORD& dwRef) const;
```

### <a name="parameters"></a>參數

*德夫里夫*<br/>
對將接收定位器類型的 DWORD 的引用。 有關定位器類型表,請參閱**備註**。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果調用失敗,可能會調用 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)以確定錯誤的原因。

### <a name="remarks"></a>備註

可能的類型如下:

|值|意義|
|-----------|-------------|
|GOPHER_TYPE_TEXT_FILE|ASCII 文字檔。|
|GOPHER_TYPE_DIRECTORY|其他 Gopher 項的目錄。|
|GOPHER_TYPE_CSO|CSO 電話簿伺服器。|
|GOPHER_TYPE_ERROR|指示錯誤條件。|
|GOPHER_TYPE_MAC_BINHEX|BINHEX 格式的 Macintosh 檔。|
|GOPHER_TYPE_DOS_ARCHIVE|DOS 存檔檔。|
|GOPHER_TYPE_UNIX_UUENCODED|UUENCODED 檔。|
|GOPHER_TYPE_INDEX_SERVER|索引伺服器。|
|GOPHER_TYPE_TELNET|電話網伺服器。|
|GOPHER_TYPE_BINARY|二進位檔。|
|GOPHER_TYPE_REDUNDANT|複製的伺服器。 中包含的資訊是主伺服器的重複項。 主伺服器是最後一個沒有GOPHER_TYPE_REDUNDANT類型的目錄條目。|
|GOPHER_TYPE_TN3270|TN3270 伺服器。|
|GOPHER_TYPE_GIF|GIF 圖形檔。|
|GOPHER_TYPE_IMAGE|圖像檔。|
|GOPHER_TYPE_BITMAP|位圖檔。|
|GOPHER_TYPE_MOVIE|影片檔。|
|GOPHER_TYPE_SOUND|聲音檔。|
|GOPHER_TYPE_HTML|HTML 文件。|
|GOPHER_TYPE_PDF|PDF 檔。|
|GOPHER_TYPE_CALENDAR|日曆檔。|
|GOPHER_TYPE_INLINE|內聯檔。|
|GOPHER_TYPE_UNKNOWN|項類型未知。|
|GOPHER_TYPE_ASK|問+專案。|
|GOPHER_TYPE_GOPHER_PLUS|戈弗斯*專案。|

## <a name="cgopherlocatoroperator-lpctstr"></a><a name="operator_lpctstr"></a>CGopher定位器::操作員LPCTSTR

此有用的強制轉換運算符提供存取`CGopherLocator`物件中包含的空端接 C 字串的有效方法。

```
operator LPCTSTR () const;
```

### <a name="return-value"></a>傳回值

指向字串資料的字元指標。

### <a name="remarks"></a>備註

不複製任何字元;僅返回指標。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind 類別](../../mfc/reference/cgopherfilefind-class.md)
