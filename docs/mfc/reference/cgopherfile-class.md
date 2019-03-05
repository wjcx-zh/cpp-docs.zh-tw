---
title: CGopherFile 類別
ms.date: 11/04/2016
f1_keywords:
- CGopherFile
- AFXINET/CGopherFile
- AFXINET/CGopherFile::CGopherFile
helpviewer_keywords:
- CGopherFile [MFC], CGopherFile
ms.assetid: 3ca9898f-8cdb-4495-bbde-46d40100feda
ms.openlocfilehash: 9bb242cb53593862cb51e0c193eb739625127adc
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285187"
---
# <a name="cgopherfile-class"></a>CGopherFile 類別

提供在 Gopher 伺服器上尋找和讀取檔案的功能。

> [!NOTE]
>  類別`CGopherConnection`， `CGopherFile`， `CGopherFileFind`，`CGopherLocator`和其成員已被取代，因為它們不在 Windows XP 平台上運作，但它們會繼續在舊版平台上運作。

## <a name="syntax"></a>語法

```
class CGopherFile : public CInternetFile
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[CGopherFile::CGopherFile](#cgopherfile)|建構 `CGopherFile` 物件。|

## <a name="remarks"></a>備註

Gopher 服務不允許使用者將資料寫入至 gopher 檔案，因為這項服務主要是做為尋找資訊的功能表導向介面。 `CGopherFile`成員函式`Write`， `WriteString`，以及`Flush`並未實作`CGopherFile`。 在呼叫這些函式`CGopherFile`物件，會傳回[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。

若要進一步了解如何`CGopherFile`運作方式與其他 MFC 網際網路類別，請參閱文章[網際網路程式設計 WinInet](../../mfc/win32-internet-extensions-wininet.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

[CInternetFile](../../mfc/reference/cinternetfile-class.md)

`CGopherFile`

## <a name="requirements"></a>需求

**標頭：** afxinet.h

##  <a name="cgopherfile"></a>  CGopherFile::CGopherFile

此成員函式呼叫來建構`CGopherFile`物件。

```
CGopherFile(
    HINTERNET hFile,
    CGopherLocator& refLocator,
    CGopherConnection* pConnection);

CGopherFile(
    HINTERNET hFile,
    HINTERNET hSession,
    LPCTSTR pstrLocator,
    DWORD dwLocLen,
    DWORD_PTR dwContext);
```

### <a name="parameters"></a>參數

*hFile*<br/>
HINTERNET 檔案控制代碼。

*refLocator*<br/>
參考[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)物件。

*pConnection*<br/>
指標[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)物件。

*hSession*<br/>
目前的網際網路工作階段控制代碼。

*pstrLocator*<br/>
用來找出 gopher 伺服器的字串指標。 請參閱[Gopher 工作階段](cgopherlocator-class.md)的 gopher 定位器的詳細資訊。

*dwLocLen*<br/>
DWORD，其中包含數字中的位元組*pstrLocator*。

*dwContext*<br/>
正在開啟之檔案的內容識別碼指標。

### <a name="remarks"></a>備註

您需要`CGopherFile`gopher 網際網路工作階段期間從檔案讀取物件。

您永遠不會建立`CGopherFile`直接物件。 請改為呼叫[CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile)至 gopher 伺服器上開啟檔案。

## <a name="see-also"></a>另請參閱

[CInternetFile 類別](../../mfc/reference/cinternetfile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CInternetFile 類別](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherLocator 類別](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopherFileFind 類別](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CGopherConnection 類別](../../mfc/reference/cgopherconnection-class.md)
