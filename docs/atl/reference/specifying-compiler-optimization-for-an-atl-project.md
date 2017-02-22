---
title: "為 ATL 專案指定編譯器最佳化 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.appwiz.ATL.optimization"
  - "vc.appwiz.ATL.vtable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 專案, 編譯器最佳化"
  - "ATL_DISABLE_NO_VTABLE 巨集"
  - "ATL_NO_VTABLE 巨集"
ms.assetid: 7f379318-66d5-43dd-a53d-530758d3a228
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 為 ATL 專案指定編譯器最佳化
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

依預設，[ATL 控制項精靈](../../atl/reference/atl-control-wizard.md)會產生具有 ATL\_NO\_VTABLE 巨集的新類別，如下所示：  
  
```  
class ATL_NO_VTABLE CProjName  
{  
   ...  
};  
```  
  
 接著 ATL 會定義 \_ATL\_NO\_VTABLE，如下所示：  
  
```  
#ifdef _ATL_DISABLE_NO_VTABLE  
   #define ATL_NO_VTABLE  
#else  
   #define ATL_NO_VTABLE __declspec(novtable)  
#endif  
```  
  
 如果您未定義 \_ATL\_DISABLE\_NO\_VTABLE，ATL\_NO\_VTABLE 巨集會展開為 `declspec(novtable)`。  在類別宣告中使用 `declspec(novtable)` 將會避免 vtable 指標在類別建構函式 \(Constructor\) 和解構函式 \(Destructor\) 中初始化。  當您建置專案時，連結器 \(Linker\) 會排除 vtable 指向的 vtable 和所有函式。  
  
 您必須只在不是直接可建的基底函式上使用 ATL\_NO\_VTABLE 並接著使用 `declspec(novtable)`。  您無法在專案中衍生程度最高的類別上使用 `declspec(novtable)`，因為這個類別 \(通常是 [CComObject](../../atl/reference/ccomobject-class.md)、[CComAggObject](../../atl/reference/ccomaggobject-class.md) 或 [CComPolyObject](../../atl/reference/ccompolyobject-class.md)\) 會為專案初始化 vtable 指標。  
  
 您無法從任何使用 `declspec(novtable)` 物件之建構函式呼叫 Virtual 函式。  您必須將這些呼叫移至 [FinalConstruct](../Topic/CComObjectRootEx::FinalConstruct.md) 方法。  
  
 如果不確定是否應使用 `declspec(novtable)` 修飾詞 \(Modifier\)，您可從任何類別定義移除 ATL\_NO\_VTABLE 巨集，或是可在 stdafx.h 中指定以下這一行來全域停用它：  
  
```  
#define _ATL_DISABLE_NO_VTABLE  
```  
  
 在 stdafx.h 中，必須在包含所有其他 ATL 標頭檔 \(Header File\) 之前這麼做。  
  
## 請參閱  
 [ATL 專案精靈](../../atl/reference/atl-project-wizard.md)   
 [Visual C\+\+ 專案類型](../../ide/visual-cpp-project-types.md)   
 [使用應用程式精靈建立桌面專案](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [使用 ATL 和 C 執行階段程式碼進行程式設計](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Fundamentals of ATL COM Objects](../../atl/fundamentals-of-atl-com-objects.md)   
 [novtable](../../cpp/novtable.md)   
 [預設的 ATL 專案組態](../../atl/reference/default-atl-project-configurations.md)