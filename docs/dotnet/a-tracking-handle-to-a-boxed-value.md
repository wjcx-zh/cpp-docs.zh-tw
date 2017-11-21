---
title: "Boxed 值的追蹤控制代碼 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: boxed value types, tracking handle to
ms.assetid: 16c92048-5b74-47d5-8eca-dfea3d38879a
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a986dcea2eec183ae09eb9af275082922257ef76
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="a-tracking-handle-to-a-boxed-value"></a>Boxed 值的追蹤控制代碼
參考實值類型的追蹤控制代碼的使用方式已經從 Managed Extensions for c + + Visual c + +。  
  
 Boxing 是整合的 CLR 型別系統的審視。 實值類型直接包含其狀態，而參考型別都隱含的配對： 具名的實體是未命名的物件，在 managed 堆積上配置的控制代碼。 初始化或指派值的型別`Object`，例如，需要實值型別置於 CLR 堆積-這是其中 boxing 它的映像，就會發生的第一次配置相關聯的記憶體，則藉由複製值類型的狀態然後傳回此匿名值/參考混合式的位址。 因此，當其中一個寫入 C# 中  
  
```  
object o = 1024; // C# implicit boxing  
```  
  
 還有許多看起來由明顯簡化程式碼。 C# 的設計會隱藏複雜度，不僅的哪些作業會發生在幕後，但 boxing 本身抽象。 Managed 而言，這會導致效率的感應，所需要的明確指令來將它放在使用者的字體的 c + +，相反地，擴充：  
  
```  
Object *o = __box( 1024 ); // Managed Extensions explicit boxing  
```  
  
 Boxing 是隱含 Visual c + +:  
  
```  
Object ^o = 1024; // new syntax implicit boxing  
```  
  
 `__box`關鍵字做內管理擴充功能，其中不存在的重要服務所設計，例如 C# 和 Visual Basic 的語言： 它所提供之詞彙 」 和 「 追蹤處理的直接管理 managed 堆積上的已封裝的執行個體。 例如，請考慮下列的小程式：  
  
```  
int main() {  
   double result = 3.14159;  
   __box double * br = __box( result );  
  
   result = 2.7;   
   *br = 2.17;     
   Object * o = br;  
  
   Console::WriteLine( S"result :: {0}", result.ToString() ) ;  
   Console::WriteLine( S"result :: {0}", __box(result) ) ;  
   Console::WriteLine( S"result :: {0}", br );  
}  
```  
  
 產生的三個引動過程的基礎程式碼`WriteLine`顯示成本的存取的 boxed 實值類型 （這點受惠 Yves Dolce 指出這些差異的)，其中的指示的行顯示每個相關聯的額外負荷引動過程。  
  
```  
// Console::WriteLine( S"result :: {0}", result.ToString() ) ;  
ldstr      "result :: {0}"  
ldloca.s   result  // ToString overhead  
call       instance string  [mscorlib]System.Double::ToString()  // ToString overhead  
call       void [mscorlib]System.Console::WriteLine(string, object)  
  
// Console::WriteLine( S"result :: {0}", __box(result) ) ;  
Ldstr    " result :: {0}"  
ldloc.0  
box    [mscorlib]System.Double // box overhead  
call    void [mscorlib]System.Console::WriteLine(string, object)  
  
// Console::WriteLine( S"result :: {0}", br );  
ldstr    "result :: {0}"  
ldloc.0  
call     void [mscorlib]System.Console::WriteLine(string, object)  
```  
  
 Boxed 實的值類型將直接傳遞至`Console::WriteLine`排除的 boxing 和叫用需要`ToString()`。 (當然，沒有舊版的 boxing 初始化`br`，因此我們不除非我們真的將取得的任何項目`br`運作。  
  
 在新語法中，對 boxed 實的值類型的支援會是更加簡潔，而且型別系統中的整合式同時保留其電源。 例如，以下是舊版的小程式中的轉譯：  
  
```  
int main()  
{  
   double result = 3.14159;  
   double^ br = result;  
   result = 2.7;  
   *br = 2.17;  
   Object^ o = br;  
   Console::WriteLine( "result :: {0}", result.ToString() );  
   Console::WriteLine( "result :: {0}", result );  
   Console::WriteLine( "result :: {0}", br );  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [實值類型和它們的行為 (C + + /CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [如何：明確要求 Boxing](../dotnet/how-to-explicitly-request-boxing.md)