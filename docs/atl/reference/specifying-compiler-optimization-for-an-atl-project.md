---
title: "指定 ATL 專案的編譯器最佳化 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.optimization
- vc.appwiz.ATL.vtable
dev_langs: C++
helpviewer_keywords:
- ATL_DISABLE_NO_VTABLE macro
- ATL projects, compiler optimization
- ATL_NO_VTABLE macro
ms.assetid: 7f379318-66d5-43dd-a53d-530758d3a228
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0b9b3d6b3fabe2a24a4b296709e835d07a63e441
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="specifying-compiler-optimization-for-an-atl-project"></a>指定 ATL 專案的編譯器最佳化
根據預設， [ATL 控制項精靈](../../atl/reference/atl-control-wizard.md)會產生與 ATL_NO_VTABLE 巨集的新類別，如下所示：  
  
```  
class ATL_NO_VTABLE CProjName  
{  
 ...  
};  
```  
  
 ATL 然後定義了 _ATL_NO_VTABLE，如下所示：  
  
```  
#ifdef _ATL_DISABLE_NO_VTABLE  
 #define ATL_NO_VTABLE  
#else  
 #define ATL_NO_VTABLE __declspec(novtable)  
#endif  
```  
  
 如果您沒有定義 _ATL_DISABLE_NO_VTABLE ATL_NO_VTABLE 巨集會展開`declspec(novtable)`。 使用`declspec(novtable)`在類別宣告會防止 vtable 指標在類別建構函式和解構函式中初始化。 當您建置專案時，連結器會排除在 vtable 和 vtable 所指向的所有函式。  
  
 您必須使用 ATL_NO_VTABLE，並進而`declspec(novtable)`，只有的基底類別不是直接建立。 您必須使用`declspec(novtable)`與最具衍生性的類別，在專案中，因為這個類別 (通常[Ccomobject<](../../atl/reference/ccomobject-class.md)， [CComAggObject](../../atl/reference/ccomaggobject-class.md)，或[CComPolyObject](../../atl/reference/ccompolyobject-class.md))初始化 vtable 指標為您的專案。  
  
 您必須從使用的任何物件的建構函式呼叫虛擬函式`declspec(novtable)`。 您也應該一併移動這些呼叫[跖](ccomobjectrootex-class.md#finalconstruct)方法。  

  
 如果您不確定您是否應使用`declspec(novtable)`修飾詞，您可以從任何類別定義中，移除 ATL_NO_VTABLE 巨集，或您可以全域予以停用指定  
  
```  
#define _ATL_DISABLE_NO_VTABLE  
```  
  
 在 stdafx.h 之前其他所有的 ATL, 標頭檔都包含在內。  
  
## <a name="see-also"></a>另請參閱  
 [ATL 專案精靈](../../atl/reference/atl-project-wizard.md)   
 [Visual c + + 專案類型](../../ide/visual-cpp-project-types.md)   
 [使用應用程式精靈建立桌面專案](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [ATL 和 C 執行階段程式碼的程式設計](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)   
 [novtable](../../cpp/novtable.md)   
 [預設 ATL 專案組態](../../atl/reference/default-atl-project-configurations.md)

