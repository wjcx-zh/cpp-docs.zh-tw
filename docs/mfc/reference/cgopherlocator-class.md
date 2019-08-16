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
ms.openlocfilehash: 9ce95a712af6502bff2a2502582a7fa843bf9653
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506164"
---
# <a name="cgopherlocator-class"></a>CGopherLocator 類別

從 Gopher 伺服器取得 gopher 「定位器」, 判斷定位器的類型, 並讓定位器可供[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)。

> [!NOTE]
>  類別`CGopherConnection`、 `CGopherFile`、和其成員`CGopherLocator`已被取代, 因為它們無法在 Windows XP 平臺上使用, 但它們將繼續在舊版平臺上使用。 `CGopherFileFind`

## <a name="syntax"></a>語法

```
class CGopherLocator : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CGopherLocator::CGopherLocator](#cgopherlocator)|建構 `CGopherLocator` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CGopherLocator::GetLocatorType](#getlocatortype)|剖析 gopher 定位器, 並決定其屬性。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CGopherLocator:: operator LPCTSTR](#operator_lpctstr)|直接存取以 C 樣式字串`CGopherLocator`儲存在物件中的字元。|

## <a name="remarks"></a>備註

應用程式必須先取得 Gopher 伺服器的定位器, 才能從該伺服器抓取資訊。 一旦有了定位器, 它就必須將定位器視為不透明的 token。

每個 gopher 定位器都有屬性, 可決定找到的檔或伺服器類型。 如需 gopher 定位器類型的清單, 請參閱[GetLocatorType](#getlocatortype) 。

應用程式通常會使用定位器來呼叫[CGopherFileFind:: FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) , 以取得特定的資訊片段。

若要深入瞭解如何`CGopherLocator`與其他 MFC 網際網路類別搭配運作, 請參閱[使用 WinInet 進行網際網路程式設計](../../mfc/win32-internet-extensions-wininet.md)一文。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CGopherLocator`

## <a name="requirements"></a>需求

**標頭:** afxinet.h。h

##  <a name="cgopherlocator"></a>CGopherLocator::CGopherLocator

呼叫這個成員函式以建立`CGopherLocator`物件。

```
CGopherLocator(const CGopherLocator& ref);
```

### <a name="parameters"></a>參數

*ref*<br/>
常數`CGopherLocator`物件的參考。

### <a name="remarks"></a>備註

您永遠不會`CGopherLocator`直接建立物件。 相反地, 請呼叫[CGopherConnection:: CreateLocator](../../mfc/reference/cgopherconnection-class.md#createlocator)來建立並傳回`CGopherLocator`物件的指標。

##  <a name="getlocatortype"></a>CGopherLocator::GetLocatorType

呼叫這個成員函式以取得定位器類型。

```
BOOL GetLocatorType(DWORD& dwRef) const;
```

### <a name="parameters"></a>參數

*dwRef*<br/>
將接收定位器型別之 DWORD 的參考。 如需定位器類型的資料表, 請參閱**備註**。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。 如果呼叫失敗, 則可以呼叫 Win32 函數[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)來判斷錯誤的原因。

### <a name="remarks"></a>備註

可能的類型如下所示:

|值|意義|
|-----------|-------------|
|GOPHER_TYPE_TEXT_FILE|ASCII 文字檔。|
|GOPHER_TYPE_DIRECTORY|其他 Gopher 專案的目錄。|
|GOPHER_TYPE_CSO|CSO 電話簿伺服器。|
|GOPHER_TYPE_ERROR|表示錯誤狀況。|
|GOPHER_TYPE_MAC_BINHEX|BINHEX 格式的 Macintosh 檔案。|
|GOPHER_TYPE_DOS_ARCHIVE|DOS 封存檔案。|
|GOPHER_TYPE_UNIX_UUENCODED|UUENCODE 編碼檔案。|
|GOPHER_TYPE_INDEX_SERVER|索引伺服器。|
|GOPHER_TYPE_TELNET|Telnet 伺服器。|
|GOPHER_TYPE_BINARY|二進位檔案。|
|GOPHER_TYPE_REDUNDANT|重複的伺服器。 內所包含的資訊是主伺服器的複本。 主伺服器是最後一個沒有 GOPHER_TYPE_REDUNDANT 類型的目錄專案。|
|GOPHER_TYPE_TN3270|TN3270 伺服器。|
|GOPHER_TYPE_GIF|GIF 圖形檔案。|
|GOPHER_TYPE_IMAGE|影像檔案。|
|GOPHER_TYPE_BITMAP|點陣圖檔案。|
|GOPHER_TYPE_MOVIE|電影檔案。|
|GOPHER_TYPE_SOUND|音效檔。|
|GOPHER_TYPE_HTML|HTML 文件。|
|GOPHER_TYPE_PDF|PDF 檔案。|
|GOPHER_TYPE_CALENDAR|行事曆檔案。|
|GOPHER_TYPE_INLINE|內嵌檔案。|
|GOPHER_TYPE_UNKNOWN|專案類型不明。|
|GOPHER_TYPE_ASK|Ask + 專案。|
|GOPHER_TYPE_GOPHER_PLUS|Gopher + 專案。|

##  <a name="operator_lpctstr"></a>CGopherLocator:: operator LPCTSTR

這個有用的轉型運算子提供有效率的方法來存取`CGopherLocator`物件中包含之以 null 終止的 C 字串。

```
operator LPCTSTR () const;
```

### <a name="return-value"></a>傳回值

字串資料的字元指標。

### <a name="remarks"></a>備註

不會複製任何字元;只會傳回指標。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind 類別](../../mfc/reference/cgopherfilefind-class.md)
