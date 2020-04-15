---
title: OLE 初始化
ms.date: 11/04/2016
f1_keywords:
- afxdisp/AfxOleInit
- afxdisp/AfxEnableControlContainer
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
ms.openlocfilehash: 39a6f28bfe38f254f15f441ed6305daa2cb5793e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373038"
---
# <a name="ole-initialization"></a>OLE 初始化

應用程式必須先初始化 OLE 系統 DLL 並驗證 DLL 版本是否正確，才可以使用 OLE 系統服務。 該`AfxOleInit`函數初始化 OLE 系統 DLL。

### <a name="ole-initialization"></a>OLE 初始化

|||
|-|-|
|[AfxOleInit](#afxoleinit)|初始化 OLE 程式庫。|
|[AfxEnableControlContainer](#afxenablecontrolcontainer)|呼叫應用程式物件的 `InitInstance` 函式中的這個函式，可支援 OLE 控制項的內含項目。|

## <a name="afxenablecontrolcontainer"></a><a name="afxenablecontrolcontainer"></a>Afxenable 控制容器

呼叫應用程式物件的 `InitInstance` 函式中的這個函式，可支援 OLE 控制項的內含項目。

### <a name="syntax"></a>語法

```
void AfxEnableControlContainer( );
```

### <a name="remarks"></a>備註

有關 OLE 控制項(現在稱為 ActiveX 控制項)的詳細資訊,請參閱[ActiveX 控制件主題](../mfc-activex-controls.md)。

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="afxoleinit"></a><a name="afxoleinit"></a>阿FXOleinit

初始化應用程式的 OLE 支援。

```
BOOL AFXAPI AfxOleInit();
```

### <a name="return-value"></a>傳回值

如果成功,則非零;如果初始化失敗,則為 0,可能是因為安裝了不正確的 OLE 系統 DLL 版本。

### <a name="remarks"></a>備註

調用此函數以初始化 MFC 應用程式的 OLE 支援。 呼叫此函數時,將執行以下操作:

- 在調用應用程式的當前單元上初始化 COM 庫。 有關詳細資訊,請參閱[Ole 初始化](/windows/win32/api/ole2/nf-ole2-oleinitialize)。

- 創建消息篩選器物件,實現[IMessageFilter](/windows/win32/api/objidl/nn-objidl-imessagefilter)介面。 此消息篩選器可通過調用[AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter)進行訪問。

> [!NOTE]
> 如果從 MFC DLL 調用**AfxOleInit,** 則呼叫將失敗。 發生失敗的原因是,如果函數從 DLL 調用,則以前調用應用程式會初始化 OLE 系統。

> [!NOTE]
> MFC 應用程式必須初始化為單線程單元 (STA)。 如果在`InitInstance`重寫中調用[Co 初始化 Ex,](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex)請指定COINIT_APARTMENTTHREADED(而不是COINIT_MULTITHREADED)。

### <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
