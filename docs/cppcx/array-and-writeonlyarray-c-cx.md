---
title: "Array 和 WriteOnlyArray (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ef7cc5f9-cae6-4636-8220-f789e5b6aea4
caps.latest.revision: 28
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 28
---
# Array 和 WriteOnlyArray (C++/CX)
您可以在 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 程式中任意使用標準 C\-Style 陣列或 [std::array](../standard-library/array-class-stl.md) \(雖然 [std::vector](../Topic/vector%20Class%201.md) 通常是比較好的選擇\)，但若是在中繼資料中所發行的任何 API 中，您必須根據 C\-Style 陣列或向量的用途，將其轉換為 [Platform::Array](../cppcx/platform-array-class.md) 或 [Platform::WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md) 類型。[Platform::Array](../cppcx/platform-array-class.md) 類型的效率及功能都不如 [std::vector](../Topic/vector%20Class%201.md)，因此一般來說，您應該避免在對陣列元素執行許多作業的內部程式碼中使用此類型。  
  
 下列陣列類型可以透過 ABI 傳遞：  
  
1.  const Platform::Array^  
  
2.  Platform::Array^\*  
  
3.  Platform::WriteOnlyArray  
  
4.  Platform::Array^ 的傳回值  
  
 您可以使用這些陣列類型，實作 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]所定義的三種陣列模式類型。  
  
 PassArray  
 當呼叫端將陣列傳遞給方法時使用。 C\+\+ 輸入參數類型為 `const`[Platform::Array](../cppcx/platform-array-class.md)\<T\>。  
  
 FillArray  
 當呼叫端傳遞陣列供方法填入時使用。 C\+\+ 輸入參數類型為 [Platform::WriteOnlyArray](../cppcx/platform-writeonlyarray-class.md)\<T\>。  
  
 ReceiveArray  
 當呼叫端接收方法所配置的陣列時使用。 在 C\+\+\/CX 中，您可以傳回值 Array^ 傳回陣列，也可以傳回做為 Array^ 類型的 out 參數。  
  
## PassArray 模式  
 當用戶端程式碼將陣列傳遞至 C\+\+ 方法，且這個方法不會修改陣列時，這個方法會以 const Array^ 形式接受陣列。 在 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 應用程式二進位介面 \(ABI\) 層級，這稱為 PassArray。 下一個範例顯示如何將 JavaScript 中配置的陣列傳遞至讀取此陣列的 C\+\+ 函式。  
  
 [!code-javascript[cx_arrays#101](../snippets/javascript/VS_Snippets_Misc/cx_arrays/javascript/default.js#101)]  
  
 下列程式碼片段示範 C\+\+ 方法：  
  
 [!code-cpp[cx_arrays#01](../snippets/cpp/VS_Snippets_Misc/cx_arrays/cpp/class1.cpp#01)]  
  
## ReceiveArray 模式  
 在 ReceiveArray 模式中，用戶端程式碼會宣告陣列，並將它傳遞至為它配置記憶體並初始化的方法。 C\+\+ 輸入參數類型為 Hat 指標：`Array<T>^*`。 下列範例顯示如何在 JavaScript 中宣告陣列物件，並將它傳遞至 C\+\+ 函式，此函式會配置記憶體、初始化元素，然後將它傳回至 JavaScript。 JavaScript 將配置的陣列視為傳回值，但 C\+\+ 函式將它視為 out 參數。  
  
 [!code-javascript[cx_arrays#102](../snippets/javascript/VS_Snippets_Misc/cx_arrays/javascript/default.js#102)]  
  
 下列程式碼片段示範實作 C\+\+ 方法的兩種方式：  
  
 [!code-cpp[cx_arrays#02](../snippets/cpp/VS_Snippets_Misc/cx_arrays/cpp/class1.cpp#02)]  
  
## 填入陣列  
 當您想要在呼叫端配置陣列，並在被呼叫端初始化或修改它時，請使用 `WriteOnlyArray`。 下一個範例顯示如何實作使用 `WriteOnlyArray` 的 C\+\+ 函式，以及從 JavaScript 呼叫此函式。  
  
 [!code-javascript[cx_arrays#103](../snippets/javascript/VS_Snippets_Misc/cx_arrays/javascript/default.js#103)]  
  
 下列程式碼片段示範如何實作 C\+\+ 方法：  
  
 [!code-cpp[cx_arrays#03](../snippets/cpp/VS_Snippets_Misc/cx_arrays/cpp/class1.cpp#03)]  
  
## 陣列轉換  
 下列範例顯示如何使用 [Platform::Array](../cppcx/platform-array-class.md) 來建構其他類型的集合：  
  
 [!code-cpp[cx_arrays#05](../snippets/cpp/VS_Snippets_Misc/cx_arrays/cpp/class1.cpp#05)]  
  
 下一個範例顯示如何從 C\-Style 陣列建構 [Platform::Array](../cppcx/platform-array-class.md)，並從公用方法中傳回它。  
  
 [!code-cpp[cx_arrays#06](../snippets/cpp/VS_Snippets_Misc/cx_arrays/cpp/class1.cpp#06)]  
  
## 不規則陣列  
 Windows 執行階段類型系統不支援不規則陣列的概念，因此您也就不能使用 `IVector<Platform::Array<T>>` 做為公用方法的傳回值或方法參數。 若要跨 ABI 傳遞不規則陣列或一組序列中的某個序列，請使用 `IVector<IVector<T>^>`。  
  
## 使用 ArrayReference 可避免複製資料  
 在透過 ABI 傳遞資料給 [Platform::Array](../cppcx/platform-array-class.md)，且您最終需要在 C\-Style 陣列中處理資料以提升效率的某些情況下，您可以使用 [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) 避免額外的複製作業。 當您將 [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) 當做引數傳遞給採用 `Platform::Array` 的參數時，`ArrayReference` 會將資料直接儲存到您指定的 C\-Style 陣列中。 請注意，`ArrayReference` 不會鎖定來源資料，因此如果在呼叫完成之前修改或刪除另一個執行緒上的資料，結果會是未定義的。  
  
 下列程式碼片段示範如何將 [DataReader](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.datareader.aspx) 作業的結果複製到 `Platform::Array` 中 \(一般模式\)，以及如何接著替代 `ArrayReference`，將資料直接複製到 C\-Style 陣列中：  
  
 [!code-cpp[cx_arrays#07](../snippets/cpp/VS_Snippets_Misc/cx_arrays/cpp/class1.h#07)]  
  
## 避免將陣列公開為屬性  
 一般而言，您應該避免將 `Platform::Array` 類型公開為 ref 類別中的屬性，因為即使用戶端程式碼只嘗試存取單一元素，也會傳回整個陣列。 當您必須將序列容器公開為公用 ref 類別中的屬性時，[Windows::Foundation::IVector](http://msdn.microsoft.com/library/windows/apps/br206631.aspx) 會是較佳選擇。 在私用或內部應用程式開發介面中 \(不會發行到中繼資料\)，請考慮使用 Standard C\+\+ 容器，例如 [std::vector](../Topic/vector%20Class%201.md)。  
  
## 請參閱  
 [類型系統](../cppcx/type-system-c-cx.md)   
 [Visual C\+\+ 語言參考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空間參考](../cppcx/namespaces-reference-c-cx.md)