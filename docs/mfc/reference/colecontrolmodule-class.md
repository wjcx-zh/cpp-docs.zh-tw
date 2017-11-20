---
title: "COleControlModule 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: OleControlModule
dev_langs: C++
helpviewer_keywords:
- OLE control modules [MFC]
- MFC ActiveX controls [MFC], OLE control modules
- COleControlModule class [MFC]
- control modules [MFC]
ms.assetid: 0721724d-d4af-4eda-ad34-5a2b27810dd4
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0153adbae458d0f4ab432c2c7cb8c71621d76418
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="colecontrolmodule-class"></a>COleControlModule 類別
OLE 控制項模組物件所衍生自的基底類別。  
  
## <a name="syntax"></a>語法  
  
```  
class COleControlModule : public CWinApp  
```  
  
## <a name="remarks"></a>備註  
 這個類別提供成員函式初始化控制項模組。 使用 Microsoft Foundation classes 每個 OLE 控制項模組只能包含一個物件衍生自`COleControlModule`。 其他 c + + 的全域物件建構時，會建構這個物件。 宣告衍生`COleControlModule`全域層級的物件。  
  
 如需有關使用`COleControlModule`類別，請參閱[CWinApp](../../mfc/reference/cwinapp-class.md)類別和文章[ActiveX 控制項](../../mfc/mfc-activex-controls.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWinThread](../../mfc/reference/cwinthread-class.md)  
  
 [CWinApp](../../mfc/reference/cwinapp-class.md)  
  
 `COleControlModule`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxctl.h  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 TESTHELP](../../visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)



