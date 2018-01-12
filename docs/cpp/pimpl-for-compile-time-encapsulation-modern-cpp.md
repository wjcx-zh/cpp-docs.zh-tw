---
title: "（現代 c + +） 的編譯時間封裝的 Pimpl |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: c3e8a90a-b328-4990-82bb-e1b147f76e07
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6a109015f3d30b04eaf89e769e1265c49663599f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="pimpl-for-compile-time-encapsulation-modern-c"></a>編譯時間封裝的 Pimpl (現代 C++)
*Pimpl 慣用語*是現代 c + + 技巧隱藏降到最低的結合程度，並將介面的實作。 Pimpl 會簡稱為 「 指標來實作。 」 您可能已經熟悉概念，但知道的其他名稱，例如 Cheshire Cat 或編譯器防火牆慣用語。  
  
## <a name="why-use-pimpl"></a>為何要使用 pimpl？  
 以下是如何 pimpl 慣用語可以改善軟體開發生命週期：  
  
-   編譯相依性的最小化。  
  
-   分離的介面和實作。  
  
-   可攜性。  
  
## <a name="pimpl-header"></a>Pimpl 標頭  
  
```cpp  
// my_class.h  
class my_class {  
   //  ... all public and protected stuff goes here ...  
private:  
   class impl; unique_ptr<impl> pimpl; // opaque type here  
};  
  
```  
  
 Pimpl 慣用語可避免重建串聯，聯集並不可靠的物件配置。 它非常適合 （間接） 常用的型別。  
  
## <a name="pimpl-implementation"></a>Pimpl 實作  
 定義`impl`在.cpp 檔案中的類別。  
  
```cpp  
// my_class.cpp  
class my_class::impl {  // defined privately here  
  // ... all private data and functions: all of these  
  //     can now change without recompiling callers ...  
};  
my_class::my_class(): pimpl( new impl )  
{  
  // ... set impl values ...   
}  
```  
  
## <a name="best-practices"></a>最佳做法  
 請考慮是否要加入非擲回交換特製化的支援。  
  
## <a name="see-also"></a>請參閱  
 [歡迎回到 c + +](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C + + 語言參考](../cpp/cpp-language-reference.md)   
 [C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)