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
ms.openlocfilehash: 61e8442c085a5be0a7266409daf973bf63f52a7f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505509"
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

|名稱|說明|
|----------|-----------------|
|[CMetaFileDC::Close](#close)|關閉裝置內容, 並建立中繼檔控制碼。|
|[CMetaFileDC::CloseEnhanced](#closeenhanced)|關閉增強型中繼檔裝置內容, 並建立增強型中繼檔控制碼。|
|[CMetaFileDC::Create](#create)|建立 Windows 中繼檔裝置內容, 並將其附加`CMetaFileDC`至物件。|
|[CMetaFileDC::CreateEnhanced](#createenhanced)|建立增強格式中繼檔的中繼檔裝置內容。|

## <a name="remarks"></a>備註

若要執行 Windows 中繼檔, 請先`CMetaFileDC`建立物件。 叫用`CMetaFileDC`此函式, 然後呼叫[Create](#create)成員函式, 該函式會建立 Windows 中繼檔裝置內容`CMetaFileDC` , 並將其附加至物件。

接下來, `CMetaFileDC`將您想要重新執行的 CDC GDI 命令順序傳送給物件。 只能使用建立輸出的 GDI 命令, 例如`MoveTo`和。 `LineTo`

在您將所需的命令傳送至中繼檔之後, `Close`請呼叫成員函式, 這會關閉中繼檔裝置內容並傳回中繼檔控制碼。 然後處置`CMetaFileDC`物件。

[CDC::P laymetafile](../../mfc/reference/cdc-class.md#playmetafile)可以接著使用中繼檔控制碼, 重複播放中繼檔。 中繼檔也可以由 Windows 函式 (例如[CopyMetaFile](/windows/win32/api/wingdi/nf-wingdi-copymetafilew)) 操作, 該函式會將元檔案複製到磁片。

當不再需要中繼檔時, 請使用[DeleteMetaFile](/windows/win32/api/wingdi/nf-wingdi-deletemetafile) Windows 函數將它從記憶體中刪除。

您也可以執行`CMetaFileDC`物件, 讓它可以處理輸出呼叫和屬性 GDI 呼叫 (例如)。 `GetTextExtent` 這類中繼檔比較有彈性, 而且可以更輕鬆地重複使用一般 GDI 程式碼, 這通常是由輸出和屬性呼叫的混合所組成。 類別會從 CDC 繼承兩個`m_hDC`裝置內容: 和`m_hAttribDC`。 `CMetaFileDC` 裝置內容會處理所有[cdc](../../mfc/reference/cdc-class.md) gdi `m_hAttribDC`輸出呼叫, 而裝置內容會處理所有 cdc gdi 屬性呼叫。 `m_hDC` 一般來說, 這兩個裝置內容會參考相同的裝置。 在案例`CMetaFileDC`中, 屬性 DC 預設會設定為 Null。

建立第二個裝置內容, 指向螢幕、印表機或非中繼檔以外的裝置, 然後呼叫`SetAttribDC`成員函式, 將新的裝置內容與`m_hAttribDC`建立關聯。 資訊的 GDI 呼叫現在會導向至新`m_hAttribDC`的。 輸出 GDI 呼叫將會移`m_hDC`至, 代表中繼檔。

如需的詳細`CMetaFileDC`資訊, 請參閱[裝置](../../mfc/device-contexts.md)內容。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CMetaFileDC`

## <a name="requirements"></a>需求

**標頭:** afxext.h。h

##  <a name="close"></a>  CMetaFileDC::Close

關閉中繼檔裝置內容, 並建立可使用[CDC::P laymetafile](../../mfc/reference/cdc-class.md#playmetafile)成員函式來播放中繼檔的 Windows 中繼檔控制碼。

```
HMETAFILE Close();
```

### <a name="return-value"></a>傳回值

如果函式成功, 則為有效的 HMETAFILE;否則為 Null。

### <a name="remarks"></a>備註

Windows 中繼檔控制碼也可以用來操作具有 Windows 函式 (例如[CopyMetaFile](/windows/win32/api/wingdi/nf-wingdi-copymetafilew)) 的中繼檔。

藉由呼叫 Windows [DeleteMetaFile](/windows/win32/api/wingdi/nf-wingdi-deletemetafile)函數, 在使用後刪除中繼檔。

##  <a name="closeenhanced"></a>CMetaFileDC:: CloseEnhanced

關閉增強型中繼檔裝置內容, 並傳回識別增強格式中繼檔的控制碼。

```
HENHMETAFILE CloseEnhanced();
```

### <a name="return-value"></a>傳回值

增強型中繼檔的控制碼 (如果成功);否則為 Null。

### <a name="remarks"></a>備註

應用程式可以使用此函式所傳回的增強型中繼檔控制碼來執行下列工作:

- 顯示儲存在增強型中繼檔中的圖片

- 建立增強型中繼檔的複本

- 列舉、編輯或複製增強型中繼檔中的個別記錄

- 從增強的中繼檔標頭抓取中繼檔內容的選擇性描述

- 取出增強型中繼檔標頭的複本

- 取出增強型中繼檔的二進位複本

- 列舉選擇性調色板中的色彩

- 將增強格式中繼檔轉換成 Windows 格式中繼檔

當應用程式不再需要增強型中繼檔控制碼時, 它應該藉由呼叫 Win32 `DeleteEnhMetaFile`函數來釋放控制碼。

##  <a name="cmetafiledc"></a>  CMetaFileDC::CMetaFileDC

以兩個步驟來建立物件。`CMetaFileDC`

```
CMetaFileDC();
```

### <a name="remarks"></a>備註

首先, 呼叫`CMetaFileDC`, 然後呼叫`Create`, 它會建立 Windows 中繼檔裝置內容, `CMetaFileDC`並將其附加至物件。

##  <a name="create"></a>  CMetaFileDC::Create

以兩個步驟來建立物件。`CMetaFileDC`

```
BOOL Create(LPCTSTR lpszFilename = NULL);
```

### <a name="parameters"></a>參數

*lpszFilename*<br/>
指向以 null 結束的字元字串。 指定要建立之中繼檔的檔案名。 如果*lpszFilename*為 Null, 就會建立新的記憶體中中繼檔。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

首先, 呼叫此`CMetaFileDC`函式, 然後呼叫`Create`, 它會建立 Windows 中繼檔裝置內容, `CMetaFileDC`並將其附加至物件。

##  <a name="createenhanced"></a>CMetaFileDC:: CreateEnhanced

建立增強格式中繼檔的裝置內容。

```
BOOL CreateEnhanced(
    CDC* pDCRef,
    LPCTSTR lpszFileName,
    LPCRECT lpBounds,
    LPCTSTR lpszDescription);
```

### <a name="parameters"></a>參數

*pDCRef*<br/>
識別增強型中繼檔的參照裝置。

*lpszFileName*<br/>
指向以 null 結束的字元字串。 指定要建立之增強型中繼檔的檔案名。 如果此參數為 Null, 則增強型中繼檔會以記憶體為基礎, 而且當物件終結或呼叫 Win32 `DeleteEnhMetaFile`函式時, 其內容會遺失。

*lpBounds*<br/>
指向[矩形](/windows/win32/api/windef/ns-windef-rect)資料結構或[CRect](../../atl-mfc-shared/reference/crect-class.md)物件, 指定要儲存在增強型中繼檔中之圖片的 HIMETRIC 單位 (以 .01-毫米增量計算) 大小。

*lpszDescription*<br/>
指向以零結束的字串, 指定建立圖片的應用程式名稱, 以及圖片的標題。

### <a name="return-value"></a>傳回值

增強型中繼檔的裝置內容控制碼 (如果成功);否則為 Null。

### <a name="remarks"></a>備註

此 DC 可以用來儲存與裝置無關的圖片。

Windows 會使用*pDCRef*參數所識別的參照裝置來記錄原先出現圖片之裝置的解析度和單位。 如果*pDCRef*參數為 Null, 則會使用目前的顯示裝置來進行參考。

`RECT` *LpBounds*參數所指向之資料結構的左側和最上層成員, 必須分別小於右邊和底部成員。 沿著矩形邊緣的點會包含在圖片中。 如果*lpBounds*為 Null, 則圖形裝置介面 (GDI) 會計算最小矩形的尺寸, 而該矩形可以括住應用程式所繪製的圖片。 應該盡可能提供*lpBounds*參數。

*LpszDescription*參數所指向的字串必須在應用程式名稱與圖片名稱之間包含 null 字元, 而且必須以兩個 null 字元結束, 例如 "XYZ Graphics Editor\0Bald Eagle\0\0", 其中 \ 0 代表null 字元。 如果*lpszDescription*為 Null, 則增強型中繼檔標頭中沒有對應的專案。

應用程式會使用此函式所建立的 DC, 將圖形圖片儲存在增強型中繼檔中。 識別此 DC 的控制碼可以傳遞至任何 GDI 函數。

應用程式在增強的中繼檔中儲存圖片之後, 即可藉由呼叫`CDC::PlayMetaFile`函式, 在任何輸出裝置上顯示圖片。 顯示圖片時, Windows 會使用*lpBounds*參數所指向的矩形, 以及參考裝置的解析度資料來定位和縮放圖片。 此函式所傳回的裝置內容包含與任何新 DC 相關聯的預設屬性。

應用程式必須使用 Win32 `GetWinMetaFileBits`函式, 將增強型中繼檔轉換成較舊的 Windows 元檔案格式。

增強型中繼檔的檔案名應該使用。EMF 延伸模組。

## <a name="see-also"></a>另請參閱

[CDC 類別](../../mfc/reference/cdc-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
