---
title: 介面 (C + + /CX) |Microsoft 文件
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 11034314-d54a-426d-923b-5ab7a6b9f8ce
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6be3b207f6bd64685f7ec1d3f6d2271ec3b83f17
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="interfaces-ccx"></a>介面 (C++/CX)
雖然 ref 類別最多可以繼承自一個具象基底類別，但它可以實作任意數目的介面類別。 介面類別 (或介面結構) 本身可以繼承 (或要求) 多個介面類別、可以多載其成員函式，也可以具有類型參數。  
  
## <a name="characteristics"></a>特性  
 介面具有這些特性：  
  
-   您必須在命名空間中宣告介面類別 (或結構)，且此介面類別 (或結構) 可以具有公用或私用存取範圍。 只有公用介面會發出至中繼資料。  
  
-   介面的成員可以包括屬性、方法和事件。  
  
-   所有介面成員都是隱含公用及虛擬的成員。  
  
-   不允許使用欄位和靜態成員。  
  
-   型別，做為屬性、 方法參數或傳回值只能是 Windows 執行階段類型。這包括基礎類型和列舉類別類型。  
  
## <a name="declaration-and-usage"></a>宣告和用法  
 下列範例顯示如何宣告介面。 請注意，介面可以宣告為類別或結構類型。  
  
 [!code-cpp[cx_interfaces#01](../cppcx/codesnippet/CPP/interfacestest/class1.h#01)]  
  
 為了實作介面，由 ref 類別或 ref 結構宣告並實作虛擬方法和屬性。 此介面和實作的 ref 類別必須使用相同的方法參數名稱，如下列範例所示：  
  
 [!code-cpp[cx_interfaces#02](../cppcx/codesnippet/CPP/interfacestest/class1.h#02)]  
  
## <a name="interface-inheritance-hierarchies"></a>介面繼承階層架構  
 介面可以繼承一或多個介面。 但是，不同於 ref 類別或結構，介面不會宣告繼承的介面成員。 如果介面 B 繼承自介面 A，而 ref 類別 C 繼承自 B，則 C 必須同時實作 A 和 B。下一個範例將提供示範。  
  
 [!code-cpp[cx_interfaces#03](../cppcx/codesnippet/CPP/interfacestest/class1.h#03)]  
  
## <a name="implementing-interface-properties-and-events"></a>實作介面屬性和事件  
 如上述範例所示，您可以使用 trivial 虛擬屬性來實作介面屬性。 您也可以在實作類別中提供自訂 getter 和 setter。  Getter 和 setter 都必須是公用的介面屬性。  
  
 [!code-cpp[cx_interfaces#04](../cppcx/codesnippet/CPP/interfacestest/class1.h#04)]  
  
 如果介面宣告 get-only 或 set-only 屬性，則實作的類別應該明確地提供 getter 或 setter。  
  
 [!code-cpp[cx_interfaces#05](../cppcx/codesnippet/CPP/interfacestest/class1.h#05)]  
  
 您也可以在實作的類別中，實作事件的自訂 add 和 remove 方法。  
  
## <a name="explicit-interface-implementation"></a>明確介面實作  
 當 ref 類別實作多個介面，且這些介面的方法具有與編譯器相同的名稱和簽章時，您可以使用下列語法明確表示實作類別方法的介面方法。  
  
 [!code-cpp[cx_interfaces#06](../cppcx/codesnippet/CPP/interfacestest/class1.h#06)]  
  
## <a name="generic-interfaces"></a>泛型介面  
 在 C + + /CX 中，`generic`關鍵字用來代表參數化的 Windows 執行階段類型。 參數化類型會在中繼資料中發出，以供使用支援類型參數之任何語言撰寫的程式碼使用。 Windows 執行階段定義一些泛型介面 — 例如， [Windows::Foundation::Collections::IVector\<T >](Windows::Foundation::Collections::IVector)— 但它不支援建立公用使用者定義的泛型介面，在 C + + /CX。 不過，您可以建立私用泛型介面。  
  
 以下是如何使用 Windows 執行階段類型，來撰寫泛型介面：  
  
-   您不可以將元件中使用者定義的泛型 `interface class` 發出至其 Windows 中繼資料檔案，因此該類別不可以具有公用存取範圍，且其他 .winmd 檔案中的用戶端程式碼無法實作該類別。 此類別可由相同元件中的非公用 ref 類別實作。 公用 ref 類別可以包含泛型介面類型做為私用成員。  
  
     下列程式碼片段示範如何宣告泛型 `interface class` ，然後在私用 ref 類別中實作，並使用 ref 類別做為公用 ref 類別的私用成員。  
  
     [!code-cpp[cx_interfaces#07](../cppcx/codesnippet/CPP/interfacestest/class1.h#07)]  
  
-   泛型介面必須遵循規範存取範圍、成員、「 *需要* 」(Requires) 關聯性、基底類別等的標準介面規則。  
  
-   泛型介面可以接受一或多個前面有 `typename` 或 `class`的泛型類型參數。 不支援非類型參數。  
  
-   型別參數可以是任何的 Windows 執行階段類型。 也就是說，類型參數可以是參考類型、實值類型、介面類別、委派、基礎類型或公用列舉類別。  
  
-   「 *封閉式泛型介面* 」(Closed Generic Interface) 是繼承自泛型介面，並指定所有類型參數之具象類型引數的介面。 只要可以使用非泛型私用介面的地方，都能使用此介面。  
  
-   「 *開放式泛型介面* 」(Open Generic Interface) 是其中有一或多個類型參數類型，尚未提供具象類型的介面。 只要可以使用類型的地方，都能使用此類型，包括做為另一個泛型介面的類型引數。  
  
-   您只能參數化整個介面，不能參數化個別的方法。  
  
-   類型參數不可受到條件約束。  
  
-   封閉式泛型介面具有隱含產生的 UUID。 使用者無法指定 UUID。  
  
-   在介面中，對目前介面的所有參考 (包括在方法參數、傳回值或屬性中) 都假設為參考目前的具現化。 例如， *IMyIntf*表示*IMyIntf\<T >*。  
  
-   當方法參數的類型是類型參數時，該參數或變數的宣告會使用類型參數的名稱而不使用任何指標、原生參考或控制代碼宣告子。 換句話說，您不需撰寫 "T^"。  
  
-   樣板化 ref 類別必須是私用類別。 這些類別可以實作泛型介面，也可以傳遞樣板參數*T*至泛型引數*T*。樣板化 ref 類別的每個具現化本身都是 ref 類別。  
  
## <a name="see-also"></a>另請參閱  
 [類型系統](../cppcx/type-system-c-cx.md)   
 [Visual c + + 語言參考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空間參考](../cppcx/namespaces-reference-c-cx.md)