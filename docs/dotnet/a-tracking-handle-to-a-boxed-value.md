---
title: "Boxed 值的追蹤控制代碼 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Boxed 實值類型, 追蹤控制代碼至"
ms.assetid: 16c92048-5b74-47d5-8eca-dfea3d38879a
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Boxed 值的追蹤控制代碼
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

從 Managed Extensions for C\+\+ 升級為 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 之後，使用追蹤控制代碼 \(Tracking Handle\) 參考實值型別 \(Value Type\) 的方式已變更。  
  
 Boxing 是 CLR 統一型別系統的一項特性。  實值型別會直接包含其狀態，而參考型別 \(Reference Type\) 則會採用隱含搭配方式：具名實體 \(Named Entity\) 是在 Managed 堆積上配置之未命名物件的控制代碼。  例如，將實值型別初始化或指派給 `Object` 時，必須將實值型別放在 CLR 堆積中 \(即其引發 Boxing 映像的所在位置\)，方式是先配置相關聯的記憶體，接著再複製實值型別的狀態，然後傳回此匿名值\/參考組合的位址。  因此，當使用者在 C\# 中撰寫下列程式碼時：  
  
```  
object o = 1024; // C# implicit boxing  
```  
  
 雖然程式碼表面看起來很簡單，但實際的執行過程要複雜許多。  C\# 的設計不僅會隱藏實際執行的作業，也會隱藏 Boxing 本身的抽取作業，因此看起來不會那麼複雜。  相反地，Managed Extensions for C\+\+ 因為擔心這會造成使用者對效率的誤解，因此會要求使用者使用明確的指令：  
  
```  
Object *o = __box( 1024 ); // Managed Extensions explicit boxing  
```  
  
 Boxing 在 [!INCLUDE[cpp_current_long](../Token/cpp_current_long_md.md)] 中為隱含：  
  
```  
Object ^o = 1024; // new syntax implicit boxing  
```  
  
 在 Managed Extensions 中，`__box` 關鍵字是做為不可或缺的服務，這是 C\# 和 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)] 等語言在設計時所缺少的服務：它可以提供在 Managed 堆積上直接操作 Boxed 執行個體 \(Instance\) 所需的詞彙和追蹤控制代碼。  例如，以下列這一小段程式為例：  
  
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
  
 針對 `WriteLine` 的三個引動過程所產生的基礎程式碼，會顯示存取 Boxed 實值型別值時的不同負擔 \(感謝 Yves Dolce 指出這些差異\)，其中所指的幾行會分別顯示與各引動過程相關聯的負擔。  
  
```  
// Console::WriteLine( S"result :: {0}", result.ToString() ) ;  
ldstr      "result :: {0}"  
ldloca.s   result  // ToString overhead  
call       instance string  [mscorlib]System.Double::ToString()  // ToString overhead  
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
  
 如果將 Boxed 實值型別直接傳遞至 `Console::WriteLine`，就可以排除 Boxing 處理，而且不需要叫用 \(Invoke\) `ToString()` \(當然，之前初始化 `br` 時已有 Boxing 處理，因此除非真的使用 `br`，否則不會有任何作用\)。  
  
 在新的語法中，Boxed 實值型別的支援更加簡潔，而且已整合到型別系統中，同時保留了原有的功能。  例如，下列就是前面那一小段程式的轉譯結果：  
  
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
  
## 請參閱  
 [實值類型和行為 \(C\+\+\/CLI\)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [如何：明確要求 Boxing](../dotnet/how-to-explicitly-request-boxing.md)