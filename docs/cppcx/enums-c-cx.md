---
title: "列舉 (C + + /CX) |Microsoft 文件"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
caps.latest.revision: "14"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: d21a887c29b792b2857d0ee546dbc9722b60a264
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="enums-ccx"></a>列舉 (C++/CX)
C + + /CX 支援`public enum class`關鍵字，類似於標準 c + + `scoped  enum`。 當您使用以 `public enum class` 關鍵字所宣告的列舉程式時，您必須使用列舉識別項來限定每一個列舉值的範圍。  
  
### <a name="remarks"></a>備註  
 不具有存取規範 (例如 `public enum class` ) 的 `public`視為標準 C++ [限定範圍列舉](../cpp/enumerations-cpp.md)。  
  
 A`public enum class`或`public enum struct`雖然 Windows 執行階段本身需要型別是 int32 或旗標列舉的 uint32 宣告可以具有任何整數類資料類型的基礎類型。 下列語法描述 `public enum class` 或 `public enum struct`的部分。  
  
 本範例示範如何定義公用列舉類別：  
  
 [!code-cpp[cx_enums#01](../cppcx/codesnippet/CPP/cpp/class1.h#01)]  
  
 下一個範例示範如何使用該類別：  
  
 [!code-cpp[cx_enums#02](../cppcx/codesnippet/CPP/cpp/class1.h#02)]  
  
### <a name="examples"></a>範例  
 下面的範例示範如何宣告列舉，  
  
 [!code-cpp[cx_enums#03](../cppcx/codesnippet/CPP/cpp/class1.h#03)]  
  
 下一個範例示範如何轉型為數值對應項及執行比較。 請注意，列舉程式 `One` 由 `Enum1` 列舉識別項界定使用範圍，列舉程式 `First` 由 `Enum2`界定範圍。  
  
 [!code-cpp[cx_enums#04](../cppcx/codesnippet/CPP/cpp/class1.h#04)]  
  
## <a name="see-also"></a>另請參閱  
 [類型系統](../cppcx/type-system-c-cx.md)   
 [Visual c + + 語言參考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空間參考](../cppcx/namespaces-reference-c-cx.md)