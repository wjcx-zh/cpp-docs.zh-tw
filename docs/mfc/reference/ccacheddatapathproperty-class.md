---
title: CCachedDataPathProperty 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::m_Cache
dev_langs:
- C++
helpviewer_keywords:
- CCachedDataPathProperty [MFC], CCachedDataPathProperty
- CCachedDataPathProperty [MFC], m_Cache
ms.assetid: 0d81356b-4fe5-43f6-aed2-2eb5a5485706
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 06a35f51b821d7c8e5b31806a96ac2bde0d0474a
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054328"
---
# <a name="ccacheddatapathproperty-class"></a>CCachedDataPathProperty 類別

實作非同步傳輸且在記憶體檔案中快取的 OLE 控制項屬性。

## <a name="syntax"></a>語法

```
class CCachedDataPathProperty : public CDataPathProperty
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CCachedDataPathProperty::CCachedDataPathProperty](#ccacheddatapathproperty)|建構 `CCachedDataPathProperty` 物件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CCachedDataPathProperty::m_Cache](#m_cache)|`CMemFile` 在其中快取資料的物件。|

## <a name="remarks"></a>備註

記憶體檔案儲存在 RAM 中，而不是在磁碟上，並可用於快速暫時的傳輸。

連同`CAysncMonikerFile`並`CDataPathProperty`，`CCachedDataPathProperty`提供使用非同步 moniker 中 OLE 控制項的功能。 具有`CCachedDataPathProperty`物件，您就能夠以非同步方式將資料傳輸 URL 或檔案的來源，然後將它儲存在記憶體檔案，透過`m_Cache`公用變數。 所有資料都會儲存在記憶體檔案中，並不需要覆寫[OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable)除非您想要等待通知和回應。 比方說，如果您要傳送大型。GIF 檔，而且想来通知您的控制項，詳細資料已送達，並且它應該重繪本身，覆寫`OnDataAvailable`進行通知。

此類別`CCachedDataPathProperty`衍生自`CDataPathProperty`。

如需如何在網際網路應用程式中使用非同步 moniker 和 ActiveX 控制項的詳細資訊，請參閱下列主題：

- [網際網路的第一個步驟： ActiveX 控制項](../../mfc/activex-controls-on-the-internet.md)

- [非同步 Moniker 的網際網路第一個步驟：](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

[CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

[CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)

`CCachedDataPathProperty`

## <a name="requirements"></a>需求

**標頭：** afxctl.h

##  <a name="ccacheddatapathproperty"></a>  CCachedDataPathProperty::CCachedDataPathProperty

建構 `CCachedDataPathProperty` 物件。

```
CCachedDataPathProperty(COleControl* pControl = NULL);

CCachedDataPathProperty(
    LPCTSTR lpszPath,
    COleControl* pControl = NULL);
```

### <a name="parameters"></a>參數

*pControl*<br/>
要與此相關聯的 ActiveX 控制項物件的指標`CCachedDataPathProperty`物件。

*lpszPath*<br/>
此路徑，可能是絕對或相對，以用來建立實際的絕對位置的屬性會參考非同步 moniker。 `CCachedDataPathProperty` 使用不是檔案名稱的 Url。 如果您想`CCachedDataPathProperty`物件檔案，在前面加上 file:// 的路徑。

### <a name="remarks"></a>備註

`COleControl`指向的物件*pControl*正由[開啟](../../mfc/reference/cdatapathproperty-class.md#open)，並且擷取衍生的類別。 如果*pControl*是 NULL，搭配使用的控制項`Open`應該設有[SetControl](../../mfc/reference/cdatapathproperty-class.md#setcontrol)。 如果*lpszPath*是 NULL 時，您可以透過路徑中傳遞`Open`，或將它與[SetPath](../../mfc/reference/cdatapathproperty-class.md#setpath)。

##  <a name="m_cache"></a>  CCachedDataPathProperty::m_Cache

包含類別檔案名稱的記憶體快取資料的所在。

```
CMemFile m_Cache;
```

### <a name="remarks"></a>備註

記憶體檔案會儲存在 RAM 中，而不是在磁碟上。

## <a name="see-also"></a>另請參閱

[CDataPathProperty 類別](../../mfc/reference/cdatapathproperty-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDataPathProperty 類別](../../mfc/reference/cdatapathproperty-class.md)
