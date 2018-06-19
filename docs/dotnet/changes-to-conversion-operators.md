---
title: 變更為轉換運算子 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- conversion operators
- operators [C++], explicit type conversion
- type conversion, explicit conversions
- conversions, explicit
- explicit keyword [C++]
ms.assetid: 9b83925c-71b7-4bd3-ac2e-843dd7c7f184
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 750d16bc6fee86d8a3f8b912cdc4c251221dffb2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33110868"
---
# <a name="changes-to-conversion-operators"></a>轉換運算子的變更
轉換運算子的語法已從 Managed Extensions for c + + Visual c + +。  
  
 其中一個範例是撰寫`op_Implicit`指定轉換。 以下是定義`MyDouble`取自語言規格：  
  
```  
__gc struct MyDouble {  
   static MyDouble* op_Implicit( int i );   
   static int op_Explicit( MyDouble* val );  
   static String* op_Explicit( MyDouble* val );   
};  
```  
  
 這指出可在指定的整數，將轉換成整數的演算法`MyDouble`係由`op_Implicit`運算子。 此外，該轉換會隱含地執行編譯器。 同樣地，指定`MyDouble`物件，這兩個`op_Explicit`運算子提供的個別演算法將該物件轉換為整數或 managed`String`實體。 不過，編譯器不會執行轉換，除非使用者明確要求。  
  
 在 C# 中，這看起來如下：  
  
```  
class MyDouble {  
   public static implicit operator MyDouble( int i );   
   public static explicit operator int( MyDouble val );  
   public static explicit operator string( MyDouble val );   
};  
```  
  
 C# 程式碼看起來更像 c + + Managed Extensions for c + + 一樣。 這不是新語法中的案例。  
  
 ISO c + + committee 導入關鍵字`explicit`，來降低非預期的結果集，例如`Array`類別可接受單一整數引數，因為維度會隱含地轉換成任何整數`Array`物件的是不是您想要的功能相同。 為防止這個情況的其中一個方法是虛擬的第二個引數的建構函式的設計用語  
  
 相反地，您不應提供一組轉換設計在 c + + 類別型別時。 最好的範例，這是標準字串類別。 隱含轉換為單一引數建構函式接受 C 樣式字串。 不過，它不提供對應的隱含轉換運算子-，轉換為字串的物件為 C 樣式字串，但是會要求明確叫用具名函式-在此情況下，使用者`c_str()`。  
  
 因此，將相關聯的轉換運算子 （以及將封裝轉換成單一的宣告形式的集合） 的隱含/明確行為似乎是原始的 c + + 支援的轉換運算子，最終導致改善`explicit`關鍵字。 轉換運算子的 Visual c + + 語言支援，如下所示，外觀的轉換演算法的隱含應用程式支援的運算子的預設行為因為這是比 C#:  
  
```  
ref struct MyDouble {  
public:  
   static operator MyDouble^ ( int i );  
   static explicit operator int ( MyDouble^ val );  
   static explicit operator String^ ( MyDouble^ val );  
};  
```  
  
 另一項變更是，單一引數的建構函式會被視為宣告為`explicit`。 這表示，以便觸發其引動過程，明確轉換，就需要。 不過請注意，是否定義明確的轉換運算子，它並沒有單一引數建構函式，會叫用。  
  
## <a name="see-also"></a>另請參閱  
 [在類別或介面中的成員宣告 (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)