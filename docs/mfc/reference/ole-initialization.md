---
title: OLE 初始化
ms.date: 11/04/2016
f1_keywords:
- afxdisp/AfxOleInit
- afxdisp/AfxEnableControlContainer
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
ms.openlocfilehash: 13c267df492ab86606e893df4c13e5510e6e546a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843686"
---
# <a name="ole-initialization"></a>OLE 初始化

應用程式必須先初始化 OLE 系統 DLL 並驗證 DLL 版本是否正確，才可以使用 OLE 系統服務。 `AfxOleInit`函數會初始化 OLE 系統 dll。

### <a name="ole-initialization"></a>OLE 初始化

|名稱|描述|
|-|-|
|[AfxOleInit](#afxoleinit)|初始化 OLE 程式庫。|
|[AfxEnableControlContainer](#afxenablecontrolcontainer)|呼叫應用程式物件的 `InitInstance` 函式中的這個函式，可支援 OLE 控制項的內含項目。|

## <a name="afxenablecontrolcontainer"></a><a name="afxenablecontrolcontainer"></a> AfxEnableControlContainer

呼叫應用程式物件的 `InitInstance` 函式中的這個函式，可支援 OLE 控制項的內含項目。

### <a name="syntax"></a>語法

```cpp
void AfxEnableControlContainer( );
```

### <a name="remarks"></a>備註

如需 OLE 控制項的詳細資訊 (現在稱為 ActiveX 控制項) ，請參閱 [Activex 控制項主題](../mfc-activex-controls.md)。

### <a name="requirements"></a>規格需求

**標頭：** afxdisp.h

## <a name="afxoleinit"></a><a name="afxoleinit"></a> AfxOleInit

初始化應用程式的 OLE 支援。

```
BOOL AFXAPI AfxOleInit();
```

### <a name="return-value"></a>傳回值

如果成功，則為非零;如果初始化失敗，可能是因為已安裝不正確的 OLE 系統 Dll 版本，則為0。

### <a name="remarks"></a>備註

呼叫此函式可初始化 MFC 應用程式的 OLE 支援。 呼叫此函式時，會發生下列動作：

- 初始化目前呼叫應用程式的單元上的 COM 程式庫。 如需詳細資訊，請參閱 [OleInitialize](/windows/win32/api/ole2/nf-ole2-oleinitialize)。

- 建立訊息篩選物件，並執行 [imessagefilter.prefiltermessage](/windows/win32/api/objidl/nn-objidl-imessagefilter) 介面。 此訊息篩選器可透過呼叫 [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter)來存取。

> [!NOTE]
> 如果從 MFC DLL 呼叫 **AfxOleInit** ，呼叫就會失敗。 發生失敗的原因是，函式假設它是從 DLL 呼叫，而 OLE 系統先前是由呼叫應用程式初始化。

> [!NOTE]
> MFC 應用程式必須初始化為單一執行緒的單元 (STA) 。 如果您在覆寫中呼叫 [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) `InitInstance` ，請指定 COINIT_APARTMENTTHREADED (，而非 COINIT_MULTITHREADED) 。

### <a name="requirements"></a>規格需求

**標頭：** afxdisp.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
