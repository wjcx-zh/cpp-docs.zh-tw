---
title: OLE 初始化 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- afxdisp/AfxOleInit
- afxdisp/AfxEnableControlContainer
dev_langs:
- C++
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b8224cf27313b056b95990f514e02eb9d9c08cad
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374720"
---
# <a name="ole-initialization"></a>OLE 初始化
應用程式必須先初始化 OLE 系統 DLL 並驗證 DLL 版本是否正確，才可以使用 OLE 系統服務。 **AfxOleInit**函式會初始化 OLE 系統 Dll。  
  
### <a name="ole-initialization"></a>OLE 初始化  
  
|||  
|-|-|  
|[AfxOleInit](#afxoleinit)|初始化 OLE 程式庫。| 
|[AfxEnableControlContainer](#afxenablecontrolcontainer)|呼叫應用程式物件的 `InitInstance` 函式中的這個函式，可支援 OLE 控制項的內含項目。| 


## <a name="afxenablecontrolcontainer"></a> AfxEnableControlContainer
呼叫應用程式物件的 `InitInstance` 函式中的這個函式，可支援 OLE 控制項的內含項目。  
   
### <a name="syntax"></a>語法    
```
void AfxEnableControlContainer( );  
```  
   
### <a name="remarks"></a>備註  
 如需 OLE 控制項 （現在稱為 ActiveX 控制項） 的詳細資訊，請參閱[ActiveX 控制項主題](../mfc-activex-controls.md)。  
   
### <a name="requirements"></a>需求  
 **標頭：** afxdisp.h  

  
##  <a name="afxoleinit"></a>  AfxOleInit  
 初始化 OLE 應用程式的支援。  
  
``` 
BOOL AFXAPI AfxOleInit(); 
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為非零如果初始化失敗，可能是因為安裝的 OLE 系統 Dll 不正確的版本是 0。  
  
### <a name="remarks"></a>備註  
 呼叫此函式以初始化 OLE 支援的 MFC 應用程式。 呼叫此函式時，執行下列動作：  
  
-   初始化 COM 程式庫上呼叫的應用程式目前的 apartment。 如需詳細資訊，請參閱[OleInitialize](http://msdn.microsoft.com/library/windows/desktop/ms690134)。  
  
-   建立訊息篩選物件，實作[IMessageFilter](http://msdn.microsoft.com/library/windows/desktop/ms693740)介面。 此訊息篩選條件可以存取透過呼叫[AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter)。  
  
> [!NOTE]
>  如果**AfxOleInit**呼叫從 MFC DLL，則呼叫會失敗。 因為函式會假設，如果呼叫的 dll，OLE 系統原先已初始化呼叫的應用程式，就會發生故障。  
  
> [!NOTE]
>  MFC 應用程式必須初始化為單一執行緒 apartment (STA)。 如果您呼叫[CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279)中您`InitInstance`覆寫中，指定`COINIT_APARTMENTTHREADED`(而非`COINIT_MULTITHREADED`)。 如需詳細資訊，請參閱 < PRB: MFC 應用程式停止回應時初始化為多執行緒 Apartment （828643） 在應用程式[ http://support.microsoft.com/default.aspxscid=kb; en-us-我們; 828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643)。  

### <a name="requirements"></a>需求  
 **標頭：** afxdisp.h

## <a name="see-also"></a>另請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)
