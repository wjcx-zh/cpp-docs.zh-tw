---
title: "OLE 初始化 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.ole
dev_langs:
- C++
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 5c2d8a1552b8cd546b7e22683fe9f73bbc54df5c
ms.lasthandoff: 02/24/2017

---
# <a name="ole-initialization"></a>OLE 初始化
應用程式必須先初始化 OLE 系統 DLL 並驗證 DLL 版本是否正確，才可以使用 OLE 系統服務。 **AfxOleInit**函式會初始化 OLE 系統 Dll。  
  
### <a name="ole-initialization"></a>OLE 初始化  
  
|||  
|-|-|  
|[AfxOleInit](#afxoleinit)|初始化 OLE 程式庫。|  
  
##  <a name="a-nameafxoleinita--afxoleinit"></a><a name="afxoleinit"></a>AfxOleInit  
 初始化 OLE 支援的應用程式。  
  
``` 
BOOL AFXAPI AfxOleInit(); 
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零如果初始化失敗，可能是因為安裝了不正確的版本，OLE 系統 Dll 的，0。  
  
### <a name="remarks"></a>備註  
 呼叫此函式以初始化 OLE 支援的 MFC 應用程式。 呼叫此函式時，執行下列動作︰  
  
-   初始化 COM 程式庫上的目前 apartment 呼叫的應用程式。 如需詳細資訊，請參閱[OleInitialize](http://msdn.microsoft.com/library/windows/desktop/ms690134)。  
  
-   建立訊息篩選物件，實作[IMessageFilter](http://msdn.microsoft.com/library/windows/desktop/ms693740)介面。 可存取此訊息篩選，藉由呼叫[AfxOleGetMessageFilter](http://msdn.microsoft.com/library/36cca011-4775-4086-b471-5557a87b266c)。  
  
> [!NOTE]
>  如果**AfxOleInit**呼叫從 MFC DLL，則呼叫會失敗。 函式假設，如果呼叫的 dll，OLE 系統所之前初始化呼叫的應用程式，就會發生失敗。  
  
> [!NOTE]
>  MFC 應用程式必須初始化為單一執行緒 apartment (STA)。 如果您呼叫[CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279)中您`InitInstance`覆寫，請指定`COINIT_APARTMENTTHREADED`(而非`COINIT_MULTITHREADED`)。 如需詳細資訊，請參閱 < PRB: MFC 應用程式停止回應時初始化為多執行緒 Apartment （828643） 在應用程式[http://support.microsoft.com/default.aspxscid=kb;en-us;828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643)。  

### <a name="requirements"></a>需求  
 **標頭：** afxdisp.h

## <a name="see-also"></a>另請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)

