---
title: ABI 界限 （現代 c + +） 上的可攜性 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c214ed18e5afec51f52514abdd73e0e5b658635a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="portability-at-abi-boundaries-modern-c"></a>ABI 界限上的可攜性 (現代 C++)
使用可攜式類型與慣例二進位介面邊界。 「可攜式類型」是一種 C 內建的類型，或是只包含 C 內建類型的結構。 類別型別只能在呼叫端和被呼叫端同意在配置，呼叫慣例，依此類推。兩者都使用相同的編譯器和編譯器設定編譯時，這樣做才可行。  
  
## <a name="how-to-flatten-a-class-for-c-portability"></a>如何簡化 C 可攜性的類別  
 當呼叫端可能會與其他編譯器/語言進行編譯，則 「 簡化 」 為**extern"C"** API 與特定的呼叫慣例：  
  
```cpp  
// class widget {  
//   widget();  
//   ~widget();  
//   double method( int, gadget& );  
// };  
extern "C" {        // functions using explicit "this"  
   struct widget;   // opaque type (forward declaration only)  
   widget* STDCALL widget_create();      // constructor creates new "this"  
   void STDCALL widget_destroy(widget*); // destructor consumes "this"  
   double STDCALL widget_method(widget*, int, gadget*); // method uses "this"  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [歡迎回到 c + +](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C + + 語言參考](../cpp/cpp-language-reference.md)   
 [C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)