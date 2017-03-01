---
title: "指定 ATL 專案的編譯器最佳化 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.optimization
- vc.appwiz.ATL.vtable
dev_langs:
- C++
helpviewer_keywords:
- ATL_DISABLE_NO_VTABLE macro
- ATL projects, compiler optimization
- ATL_NO_VTABLE macro
ms.assetid: 7f379318-66d5-43dd-a53d-530758d3a228
caps.latest.revision: 10
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
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: abdad4367e75c1971ba5d11af1a60992d1bb3dd4
ms.lasthandoff: 02/24/2017

---
# <a name="specifying-compiler-optimization-for-an-atl-project"></a>指定編譯器最佳化 ATL 專案
根據預設， [ATL 控制項精靈](../../atl/reference/atl-control-wizard.md)會產生與 ATL_NO_VTABLE 巨集的新類別，如下所示︰  
  
```  
class ATL_NO_VTABLE CProjName  
{  
 ...  
};  
```  
  
 ATL 則定義了 _ATL_NO_VTABLE，如下所示︰  
  
```  
#ifdef _ATL_DISABLE_NO_VTABLE  
 #define ATL_NO_VTABLE  
#else  
 #define ATL_NO_VTABLE __declspec(novtable)  
#endif  
```  
  
 如果沒有定義 _ATL_DISABLE_NO_VTABLE，ATL_NO_VTABLE 巨集會展開`declspec(novtable)`。 使用`declspec(novtable)`類別中宣告防止 vtable 指標在類別建構函式和解構函式中初始化。 當您建置專案時，連結器會消除 vtable 和 vtable 所指向的所有函式。  
  
 您必須使用 ATL_NO_VTABLE，並進而`declspec(novtable)`，只有的基底類別不是直接建立。 您必須使用`declspec(novtable)`與最具衍生性類別，在專案中，因為這個類別 (通常是[CComObject](../../atl/reference/ccomobject-class.md)， [CComAggObject](../../atl/reference/ccomaggobject-class.md)，或[CComPolyObject](../../atl/reference/ccompolyobject-class.md)) 初始化 vtable 指標是否為您的專案。  
  
 您不使用任何物件的建構函式呼叫虛擬函式`declspec(novtable)`。 您應該移至這些呼叫[FinalConstruct](ccomobjectrootex-class.md#finalconstruct)方法。  

  
 如果您不確定您是否應使用`declspec(novtable)`修飾詞，您可以從任何類別定義，移除 ATL_NO_VTABLE 巨集或您可以全域停用它藉由指定  
  
```  
#define _ATL_DISABLE_NO_VTABLE  
```  
  
 在 stdafx.h 之前所有其他 ATL, 標頭檔會包含。  
  
## <a name="see-also"></a>另請參閱  
 [ATL 專案精靈](../../atl/reference/atl-project-wizard.md)   
 [Visual c + + 專案類型](../../ide/visual-cpp-project-types.md)   
 [使用應用程式精靈建立桌面專案](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [使用 ATL 和 C 執行階段程式碼的程式設計](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)   
 [novtable](../../cpp/novtable.md)   
 [預設的 ATL 專案組態](../../atl/reference/default-atl-project-configurations.md)


