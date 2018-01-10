---
title: "類型轉換的 MFC 類別物件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.macros.classes
dev_langs: C++
helpviewer_keywords:
- macros [MFC], type casting
- pointers [MFC], type casting
- type casts [MFC]
- casting types [MFC]
- macros [MFC], casting pointers
ms.assetid: e138465e-c35f-4e84-b788-bd200ccf2f0e
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1fc887ad855b00b525c74b66bfc70f2adb3312e3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="type-casting-of-mfc-class-objects"></a>MFC 類別物件的類型轉換
類型轉換巨集提供一個可以指向特定類別，不論檢查合法的轉型的物件指標的指定的指標轉型。  
  
 下表列出 MFC 類型轉型巨集。  
  
### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>MFC 類別物件的指標轉型的巨集  
  
|||  
|-|-|  
|[DYNAMIC_DOWNCAST](#dynamic_downcast)|檢查是否為合法的轉型時，會轉換類別物件的指標的指標。|  
|[STATIC_DOWNCAST](#static_downcast)|從一種相關類型的指標類別會將指標轉換的物件。 在偵錯組建中，會導致**ASSERT**如果物件不是 「 種類 」 目標類型。|  
  
##  <a name="dynamic_downcast"></a>DYNAMIC_DOWNCAST  
 提供便利的類別物件的指標的指標轉型檢查是否為合法的轉型時。  
  
```   
DYNAMIC_DOWNCAST(class, pointer)  
```  
  
### <a name="parameters"></a>參數  
 `class`  
 類別的名稱。  
  
 `pointer`  
 指標轉換成的型別物件的指標`class`。  
  
### <a name="remarks"></a>備註  
 轉換巨集將`pointer`參數之物件的指標`class`參數的型別。  
  
 如果指標所參考的物件是 「 種類 」 已識別的類別，此巨集會傳回適當的指標。 如果不是合法的轉換，巨集會傳回**NULL**。  
  
##  <a name="static_downcast"></a>STATIC_DOWNCAST  
 轉型*pobject*指標*class_name*物件。  
  
```   
STATIC_DOWNCAST(class_name, pobject)   
```  
  
### <a name="parameters"></a>參數  
 *class_name*  
 轉換成類別的名稱。  
  
 *pobject*  
 要轉換成指標的指標*class_name*物件。  
  
### <a name="remarks"></a>備註  
 *pobject*必須是**NULL**，或指向的物件直接衍生的類別，或間接從*class_name*。 在您的應用程式的組建**_DEBUG**前置處理器符號定義之後，巨集將**ASSERT**如果*pobject*不**NULL**，或如果它所指向的物件不是 「 種類 」 中指定的類別*class_name*參數 (請參閱[cobject:: Iskindof](../../mfc/reference/cobject-class.md#iskindof))。 在非**_DEBUG**巨集的組建執行轉型不含任何類型檢查。  
  
 指定的類別*class_name*參數必須衍生自`CObject`，且必須使用`DECLARE_DYNAMIC`和`IMPLEMENT_DYNAMIC`、`DECLARE_DYNCREATE`和`IMPLEMENT_DYNCREATE`，或`DECLARE_SERIAL`和`IMPLEMENT_SERIAL`巨集的發行項中所述[CObject 類別： 從 CObject 衍生類別](../../mfc/deriving-a-class-from-cobject.md)。  
  
 例如，您可能會將指標轉換為`CMyDoc`，稱為`pMyDoc`，指標的**CDocument**使用下列運算式：  
  
 [!code-cpp[NVC_MFCDocView#197](../../mfc/codesnippet/cpp/type-casting-of-mfc-class-objects_1.cpp)]  
  
 如果`pMyDoc`未指向物件直接或間接衍生自**CDocument**，巨集將**ASSERT**。  
  
## <a name="see-also"></a>請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)
