---
title: "Fundamentals of ATL COM Objects | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL COM objects"
  - "ATL, COM"
  - "COM 物件, ATL"
  - "COM, 與 ATL"
ms.assetid: 0f9c9d98-cc28-45da-89ac-dc94cee422fe
caps.latest.revision: 25
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Fundamentals of ATL COM Objects
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用來定義 ATL COM 物件的下圖說明類別之間的關聯性和介面。  
  
 ![ATL 結構](../atl/media/vc307y1.png "vc307Y1")  
  
> [!NOTE]
>  圖表運算式， `CComObject``CYourClass` 從衍生，而 `CComAggObject` 和 `CComPolyObject` 包括 `CYourClass` 做為成員變數。  
  
 有三種定義 ATL COM 物件。  標準選項是使用從 `CYourClass`衍生的 `CComObject` 類別。  第二個選項是建立彙總物件使用 `CComAggObject` 類別。  第三個選項是使用 `CComPolyObject` 類別。  `CComPolyObject` 做為混合:它可以做為 `CComObject` 類別或做為 `CComAggObject` 類別，視先建立。  如需如何使用 `CComPolyObject` 類別的詳細資訊，請參閱 [CComPolyObject Class](../atl/reference/ccompolyobject-class.md)。  
  
 當您使用標準 ATL COM 時，可以使用兩個物件:外部物件和內建 \(Intrinsic\) 物件。  外部用戶端透過外部物件定義的包裝函式來存取內部物件的功能。  外部物件屬於型別 `CComObject`。  
  
 當您使用彙總物件時，外部物件為內部物件的功能會提供包裝函式。  相反地，外部物件提供外部用戶端直接存取的指標。  在這個案例中，外部物件屬於型別 `CComAggObject`。  內部物件是外部物件的成員變數，因此，它是型別 `CYourClass`。  
  
 由於用戶端不必透過外部物件與內部物件互動，彙總物件通常會更有效率。  此外，外部物件不需要了解彙總物件的功能，只要彙總物件的介面直接供用戶端使用。  不過，並非所有的物件可彙總。  如果要彙總物件，需要設計時未彙總。  
  
 以兩個階段的 ATL 實作 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) :  
  
-   [CComObject](../atl/reference/ccomobject-class.md)、 [CComAggObject](../atl/reference/ccomaggobject-class.md)或 [CComPolyObject](../atl/reference/ccompolyobject-class.md) 實作 **IUnknown** 方法。  
  
-   [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) 或 [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) 處理 **IUnknown**參考次數和外部指標。  
  
 您的 ATL COM 物件的其他方面由其他類別處理:  
  
-   [CComCoClass](../atl/reference/ccomcoclass-class.md) 定義物件的預設 Class Factory 和彙總模型。  
  
-   在[IDispatchImpl](../atl/reference/idispatchimpl-class.md) 物件提供所有雙重介面的 `IDispatch Interface` 部分的預設實作。  
  
-   [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) 實作來確定的 **ISupportErrorInfo** 介面錯誤訊息進行正確傳播呼叫鏈結。  
  
## 本章節內容  
 [實作 CComObjectRootEx](../atl/implementing-ccomobjectrootex.md)  
 顯示範例 COM 實作的 `CComObjectRootEx`對應項目。  
  
 [實作 CComObject、CComAggObject 和 CComPolyObject](../atl/implementing-ccomobject-ccomaggobject-and-ccompolyobject.md)  
 討論 **DECLARE\_\*\_AGGREGATABLE** 巨集如何影響使用 `CComObject`、 `CComAggObject`和 `CComPolyObject`。  
  
 [支援 IErrorInfo 和 IDispatch](../atl/supporting-idispatch-and-ierrorinfo.md)  
 列出實作 ATL 類別支援 `IDispatch` 和 **IErrorInfo** 介面使用。  
  
 [支援 IDispEventImpl](../atl/supporting-idispeventimpl.md)  
 討論同步實作自己的類別的連接點。  
  
 [變更預設 Class Factory 和彙總模型](../atl/changing-the-default-class-factory-and-aggregation-model.md)  
 顯示要用於巨集來變更預設 Class Factory 和彙總的模型。  
  
 [建立彙總物件](../atl/creating-an-aggregated-object.md)  
 列出使用所建立的彙總物件步驟。  
  
## 相關章節  
 [建立 ATL 專案](../atl/reference/creating-an-atl-project.md)  
 提供有關建立 ATL COM 物件的相關資訊。  
  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 使用 Active Template Library，提供概念性主題連結說明如何撰寫程式。  
  
## 請參閱  
 [概念](../atl/active-template-library-atl-concepts.md)