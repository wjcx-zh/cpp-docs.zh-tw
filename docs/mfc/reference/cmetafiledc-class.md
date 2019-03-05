---
title: CMetaFileDC 類別
ms.date: 11/04/2016
f1_keywords:
- CMetaFileDC
- AFXEXT/CMetaFileDC
- AFXEXT/CMetaFileDC::CMetaFileDC
- AFXEXT/CMetaFileDC::Close
- AFXEXT/CMetaFileDC::CloseEnhanced
- AFXEXT/CMetaFileDC::Create
- AFXEXT/CMetaFileDC::CreateEnhanced
helpviewer_keywords:
- CMetaFileDC [MFC], CMetaFileDC
- CMetaFileDC [MFC], Close
- CMetaFileDC [MFC], CloseEnhanced
- CMetaFileDC [MFC], Create
- CMetaFileDC [MFC], CreateEnhanced
ms.assetid: ffce60fa-4181-4d46-9832-25e46fad4db4
ms.openlocfilehash: 95f54f50d7a87e9a2ad4689c14f3b7f8d42ff71e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276785"
---
# <a name="cmetafiledc-class"></a>CMetaFileDC 類別

實作 Windows 中繼檔，這個檔案包含一連串可重新執行來建立所需影像或文字的繪圖裝置介面 (GDI) 命令。

## <a name="syntax"></a>語法

```
class CMetaFileDC : public CDC
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMetaFileDC::CMetaFileDC](#cmetafiledc)|建構 `CMetaFileDC` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMetaFileDC::Close](#close)|關閉裝置內容，並建立中繼檔案的控制代碼。|
|[CMetaFileDC::CloseEnhanced](#closeenhanced)|關閉增強型中繼檔裝置內容，並建立的增強型中繼檔控制代碼。|
|[CMetaFileDC::Create](#create)|建立 Windows 中繼檔裝置內容，並將它附加至`CMetaFileDC`物件。|
|[CMetaFileDC::CreateEnhanced](#createenhanced)|建立中繼檔加強格式中繼檔裝置內容。|

## <a name="remarks"></a>備註

若要實作 Windows 中繼檔，請先建立`CMetaFileDC`物件。 叫用`CMetaFileDC`建構函式，然後呼叫[建立](#create)成員函式，會建立 Windows 中繼檔裝置內容，並將它附加至`CMetaFileDC`物件。

接下來傳送`CMetaFileDC`物件您想為其重新執行的 CDC GDI 命令序列。 建立輸出，例如 GDI 命令`MoveTo`和`LineTo`，可以使用。

您所需的命令傳送至中繼檔之後，請呼叫`Close`成員函式，因此關閉中繼檔裝置內容，並傳回之中繼檔控制代碼。 然後處置`CMetaFileDC`物件。

[CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile)然後可以使用中繼檔控制代碼來重複播放之中繼檔。 中繼檔也可操作的 Windows 函式這類[CopyMetaFile](/windows/desktop/api/wingdi/nf-wingdi-copymetafilea)，這將在中繼檔複製到磁碟。

當不再需要中繼檔時，它從記憶體中刪除具有[DeleteMetaFile](/windows/desktop/api/wingdi/nf-wingdi-deletemetafile) Windows 函式。

您也可以實作`CMetaFileDC`物件，使其可以處理，同時輸出呼叫，這類屬性 GDI 呼叫`GetTextExtent`。 這類中繼檔更有彈性，可以更輕鬆地重複使用一般的 GDI 程式碼，其中通常包含混合的輸出和屬性呼叫。 `CMetaFileDC`類別會繼承兩種裝置內容，`m_hDC`和`m_hAttribDC`，從 CDC。 `m_hDC`裝置內容會處理所有[CDC](../../mfc/reference/cdc-class.md) GDI 輸出呼叫和`m_hAttribDC`裝置內容會處理 CDC GDI 屬性的所有呼叫。 一般來說，這兩個裝置的內容是指在同一部裝置。 如果是`CMetaFileDC`，DC 的屬性預設設定為 NULL。

建立指向螢幕、 印表機或裝置以外的中繼檔，然後呼叫的第二個裝置內容`SetAttribDC`成員函式來建立新的裝置內容，與關聯`m_hAttribDC`。 如需資訊的 GDI 呼叫現在會導向至新`m_hAttribDC`。 輸出 GDI 呼叫將會移至`m_hDC`，用來表示中繼檔。

如需詳細資訊`CMetaFileDC`，請參閱 <<c2> [ 裝置內容](../../mfc/device-contexts.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CMetaFileDC`

## <a name="requirements"></a>需求

**標頭：** afxext.h

##  <a name="close"></a>  CMetaFileDC::Close

關閉中繼檔裝置內容，並建立可以用來播放之中繼檔所使用的 Windows 中繼檔控制代碼[CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile)成員函式。

```
HMETAFILE Close();
```

### <a name="return-value"></a>傳回值

如果函式成功則有效 HMETAFILE否則為 NULL。

### <a name="remarks"></a>備註

Windows 中繼檔控制代碼也可用來操作 Windows 函式的中繼檔這類[CopyMetaFile](/windows/desktop/api/wingdi/nf-wingdi-copymetafilea)。

在使用後刪除中繼檔，藉由呼叫 Windows [DeleteMetaFile](/windows/desktop/api/wingdi/nf-wingdi-deletemetafile)函式。

##  <a name="closeenhanced"></a>  CMetaFileDC::CloseEnhanced

關閉增強型中繼檔裝置內容，並傳回識別格式增強型中繼檔的控制代碼。

```
HENHMETAFILE CloseEnhanced();
```

### <a name="return-value"></a>傳回值

增強型中繼檔，如果成功則控制代碼否則為 NULL。

### <a name="remarks"></a>備註

應用程式可以使用此函式所傳回的增強型中繼檔控制代碼來執行下列工作：

- 顯示儲存在加強型中繼檔圖片

- 建立增強型中繼檔的複本

- 列舉、 編輯或複製在加強型中繼檔中的個別記錄

- 從加強型中繼檔標頭擷取的中繼檔內容的選擇性描述

- 擷取一份加強型中繼檔標頭

- 擷取二進位的增強型中繼檔複本

- 列舉中的選擇性調色盤的色彩

- 轉換格式的 Windows 中繼檔加強格式中繼檔

當應用程式不再需要加強型中繼檔控制代碼時，它應該釋放控制代碼藉由呼叫 Win32`DeleteEnhMetaFile`函式。

##  <a name="cmetafiledc"></a>  CMetaFileDC::CMetaFileDC

建構`CMetaFileDC`兩個步驟中的物件。

```
CMetaFileDC();
```

### <a name="remarks"></a>備註

首先，呼叫`CMetaFileDC`，然後呼叫`Create`，這會建立 Windows 中繼檔裝置內容，並將它附加至`CMetaFileDC`物件。

##  <a name="create"></a>  CMetaFileDC::Create

建構`CMetaFileDC`兩個步驟中的物件。

```
BOOL Create(LPCTSTR lpszFilename = NULL);
```

### <a name="parameters"></a>參數

*lpszFilename*<br/>
指向以 null 結束的字元字串。 指定要建立之中繼檔的檔名。 如果*lpszFilename*為 NULL，就會建立新的記憶體中中繼檔。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

首先，呼叫建構函式`CMetaFileDC`，然後呼叫`Create`，這會建立 Windows 中繼檔裝置內容，並將它附加至`CMetaFileDC`物件。

##  <a name="createenhanced"></a>  CMetaFileDC::CreateEnhanced

建立格式增強型中繼檔裝置內容。

```
BOOL CreateEnhanced(
    CDC* pDCRef,
    LPCTSTR lpszFileName,
    LPCRECT lpBounds,
    LPCTSTR lpszDescription);
```

### <a name="parameters"></a>參數

*pDCRef*<br/>
識別參考的加強型中繼檔裝置。

*lpszFileName*<br/>
指向以 null 結束的字元字串。 指定要建立的增強型中繼檔的檔案名稱。 如果此參數為 NULL，加強型中繼檔是記憶體為基礎及其內容遺失或終結物件時 Win32`DeleteEnhMetaFile`呼叫函式。

*lpBounds*<br/>
指向[RECT](/windows/desktop/api/windef/ns-windef-tagrect)資料結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)以 himetric 為單位 （以.01 公釐） 的圖片儲存在加強型中繼檔中指定維度的物件。

*lpszDescription*<br/>
指向以零為結尾的字串，指定建立圖片，以及圖片的標題的應用程式的名稱。

### <a name="return-value"></a>傳回值

加強型中繼檔，如果成功，裝置內容控制代碼否則為 NULL。

### <a name="remarks"></a>備註

此 DC 可以用來儲存與裝置無關的圖片中。

Windows 會使用參考裝置識別*pDCRef*參數，以記錄的解析度和裝置一張圖片最初出現的單位。 如果*pDCRef*參數為 NULL，它會使用目前的顯示裝置的參考。

左邊和頂端成員`RECT`所指向的資料結構*lpBounds*參數分別必須小於右邊緣和下的成員。 邊緣的矩形中的點包含在圖片中。 如果*lpBounds*是 NULL 時，圖形裝置介面 (GDI) 計算的維度，可以將圖片繪製應用程式的最小矩形。 *LpBounds*應該盡可能提供參數。

所指向的字串*lpszDescription*參數必須包含應用程式名稱與圖片名稱之間的 null 字元，且必須終止使用兩個 null 字元，例如，"XYZ 圖形 Editor\0Bald Eagle\0\0，「 \0 表示 null 字元。 如果*lpszDescription*是 NULL，加強型中繼檔標頭中沒有任何對應的項目。

應用程式會使用此函式所建立的 DC，將圖形圖片儲存在加強型中繼檔。 識別此 DC 的控制代碼可傳遞至任何 GDI 函式。

應用程式會將圖片儲存在加強型中繼檔之後，它可以藉由呼叫任何的輸出裝置上顯示的圖片`CDC::PlayMetaFile`函式。 當顯示圖片，Windows 會使用所指的矩形*lpBounds*參數和參考裝置定位和調整圖片的解析度資料。 此函式所傳回的裝置內容會包含任何新的 DC 與相關聯的同一個預設屬性。

應用程式必須使用 Win32`GetWinMetaFileBits`加強型中繼檔轉換為較舊的 Windows 中繼檔格式的函式。

應該使用增強型中繼檔的檔名。EMF 延伸模組。

## <a name="see-also"></a>另請參閱

[CDC 類別](../../mfc/reference/cdc-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
