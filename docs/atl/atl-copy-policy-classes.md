---
title: "ATL Copy Policy Classes | Microsoft Docs"
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
  - "_Copy class"
  - "_CopyInterface class"
  - "類別 [C++], copy policy"
  - "copy policy classes [C++]"
  - "資料 [C++], ATL"
ms.assetid: 06704b68-d318-4c5d-a65b-71457fe9d00d
caps.latest.revision: 13
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL Copy Policy Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

複製原則類別是用來初始化， [公用程式類別。](../atl/utility-classes.md) 、複製和刪除資料。  複製原則類別可讓您定義任何資料型別的複製語意和定義不同的資料型別之間的轉換。  
  
 ATL 在其下範本的實作使用複製原則類別:  
  
-   [CComEnumImpl](../atl/reference/ccomenumimpl-class.md)  
  
-   [IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)  
  
-   [ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)  
  
 透過封裝必要資訊複製或轉換成可當做樣板引數的複製原則類別的資料， ATL 開發人員提供了這些類別的兩端重複使用性。  例如，在中，如果使用任意資料型別，您需要實作集合，您必須提供的是正確的複本原則;您不必連續實作集合的程式碼。  
  
## 定義  
 根據定義，提供下列靜態函式的類別是複製原則類別:  
  
 `static void init(` `DestinationType` `* p);`  
  
 `static HRESULT copy(` `DestinationType` `* pTo, const`  `SourceType` `* pFrom);`  
  
 `static void destroy(` `DestinationType` `* p);`  
  
 您可以用每項複製原則的選擇性資料型別取代型別 `DestinationType` 和 *SourceType* 。  
  
> [!NOTE]
>  雖然您可以定義複製原則為任意資料型別，它與類別的類別會使用 ATL 程式碼應該限制無意義的型別。  例如，在中，當搭配 ATL 的集合或列舉程式實作的複製原則類別， `DestinationType` 必須是可當做參數在 COM 介面方法的型別。  
  
 使用 **init** 初始化資料、 **copy** 至資料複製並 **destroy** 釋放資料。  初始化的確切意義，複製和解構是複製原則類別的網域，並根據所包含之資料型別的變更。  
  
 在使用和實作的需求複製原則類別:  
  
-   為 **copy** 的第一個參數必須只接收指標使用 **init**，您先前已初始化的資料。  
  
-   **destroy** 只接收指標至您先前已經初始化使用 **init** 或透過 **copy**已複製的資料。  
  
## 標準實作  
 以 **\_Copy** 和 **\_CopyInterface** 樣板類別 \(Class\) 的形式， ATL 提供兩個複本原則類別:  
  
-   **\_Copy** 類別允許同質只複製 \(在資料型別之間的不是轉換\)，因為它只提供一個樣板參數指定 `DestinationType` 和 *SourceType*。  這個樣板的泛用實作不包含初始化或終結程式碼並使用 `memcpy` 複製資料。  ATL 提供 **VARIANT**、 `LPOLESTR`， **OLEVERB**和 **CONNECTDATA** 資料型別也提供 **\_Copy** 的特製化。  
  
-   在標準 COM 規則之後， **\_CopyInterface** 類別提供複製之介面指標的實作。  接著這個類別允許同質只複製，因此，使用簡單的指派就和對 `AddRef` 執行該複本。  
  
## 自訂實作。  
 一般而言，您會需要定義您異質複製的自訂複製原則類別 \(也就是在資料型別之間的轉換\)。  對於自訂複製原則類別的範例，請參閱 [ATLCollections](../top/visual-cpp-samples.md) 範例的檔案 VCUE\_Copy.h 和 VCUE\_CopyString.h。  這些檔案包含兩個範本複製原則類別， `GenericCopy` 和 `MapCopy`，加上 `GenericCopy` 的特製化不同資料型別的。  
  
### GenericCopy  
 `GenericCopy` 可讓您指定 *SourceType* 和 `DestinationType` 做為樣板引數。  這 `GenericCopy` 類別的最常見的形式從 VCUE\_Copy.h 中:  
  
 [!code-cpp[NVC_ATL_COM#30](../atl/codesnippet/CPP/atl-copy-policy-classes_1.h)]  
  
 VCUE\_Copy.h 也含有下列類別的特製化: `GenericCopy_<BSTR_>`， `GenericCopy_<VARIANT, BSTR_>`， `GenericCopy_<BSTR, VARIANT_>`。  VCUE\_CopyString.h 包含重複的特製化從 **std::string**個: `GenericCopy_<std::string_>`、 `GenericCopy_<VARIANT, std::string_>`和 `GenericCopy_<BSTR, std::string_>`。  您可以提供自己的進一步特製化 `GenericCopy` 引發。  
  
### MapCopy  
 `MapCopy` 假設，複製的資料是以演算式對應會儲存，因此，它可讓您指定要儲存資料和目的型別對應的型別。  類別的實作使用 *MapType* 類別所提供的 typedef 判斷來源資料的類型和呼叫適當的 `GenericCopy` 類別。  這個類別的特製化是不需要的。  
  
 [!code-cpp[NVC_ATL_COM#31](../atl/codesnippet/CPP/atl-copy-policy-classes_2.h)]  
  
## 請參閱  
 [Implementing an STL\-Based Collection](../atl/implementing-an-stl-based-collection.md)   
 [ATLCollections 範例](../top/visual-cpp-samples.md)