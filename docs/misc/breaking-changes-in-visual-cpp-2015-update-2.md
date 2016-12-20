---
title: "Visual C++ 2015 Update 2 的重大變更 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5545ce3f-d8da-4007-88b7-8dba7dcd4d10
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "mithom"
---
# Visual C++ 2015 Update 2 的重大變更
當您升級到 Visual C\+\+ 2015 Update 2 CTP 時，先前正常編譯及執行的程式碼可能會發生編譯和\/或執行階段錯誤。 編譯器或執行階段行為中會造成這類問題的變更稱為*「重大變更」*\(breaking change\)，在進行 C\+\+ 語言標準、函式簽章或記憶體內部物件配置的修改時通常都會有重大變更。  
  
 本文的其餘部分將描述 Visual C\+\+ 2015 Update 2 CTP 中的特定重大變更，在本文中，「新行為」或「現在」等詞彙指的就是這個版本。 「舊行為」和「之前」等詞彙指的是 Visual C\+\+ 2015 Update 1 和較早的版本。 如需 Visual C\+\+ 2015 的初始版本和 Visual C\+\+ 2015 Update 1 之間的重大變更資訊，請參閱 [Update 1 的重大變更](../misc/breaking-changes-in-visual-cpp-2015-update-1.md)。 如需 Visual C\+\+ 2013 和 Visual C\+\+ 2015 之間的重大變更資訊，請參閱 [Visual C\+\+ 2015 的重大變更](../porting/visual-cpp-change-history-2003-20151.md)。  
  
-   [編譯器的重大變更](#BK_compiler)  
  
##  <a name="BK_compiler"></a> Visual C\+\+ 編譯器  
  
-   **若僅部分支援運算式 SFINAE，則可能會發出其他警告與錯誤**  
  
     舊版編譯器因為運算式 SFINAE 的支援不足，而未剖析 `decltype` 指定名稱中特定種類的運算式。 這個舊的行為不正確，而且不符合 C\+\+ 標準。 編譯器現在會剖析這些運算式，並隨著一致性逐漸改進來提供運算式 SFINAE 的部分支援。 如此一來，編譯器現在就會發出在舊版編譯器未剖析的運算式中找到的警告與錯誤。  
  
     當此新行為剖析 `decltype` 運算式 \(包含尚未宣告的型別\) 時，編譯器就會發出編譯器錯誤 C2039。  
  
 **錯誤 C2039：*'type'*: 不是 *'\`global namespace''* 的成員。**     範例 1：使用未宣告的型別 \(之前\)  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
     範例 1 \(之後\)  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
     當此新行為剖析缺少必要關鍵字 `typename` 的 `decltype` 運算式以將相依名稱指定為型別時，編譯器會發出編譯器警告 C4346 與編譯器錯誤 C2923。  
  
 **警告 C4346：*'S2\<T\>::Type'*: dependent name is not a type 錯誤 C2923：*'s1'*: *'S2\<T\>::Type'* is not a valid template type argument for parameter *'T'***     範例 2：相依名稱不是型別 \(之前\)  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
     範例 2 \(之後\)  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
-   `volatile` **成員變數會禁止隱含定義的建構函式和指派運算子**  
  
     舊版編譯器允許具有 `volatile` 成員變數的類別，自動產生預設複製\/移動建構函式和預設複製\/移動指派運算子。 這個舊的行為不正確，而且不符合 C\+\+ 標準。 編譯器現在會考慮讓具有揮發性成員變數的類別擁有非 trivial 建構和指派運算子，這樣可防止自動產生這些運算子的預設實作。  當此類別是等位 \(或類別內的匿名等位\) 的成員時，就會將等位 \(或包含 Unonymous 等位之類別\) 的複製\/移動建構函式和複製\/移動指派運算子隱含定義為已刪除。 在未明確定義的情況下，嘗試建構或複製等位 \(或包含匿名等位的類別\) 將會發生錯誤，導致編譯器發出編譯器錯誤 C2280。  
  
 **錯誤 C2280：*'B::B\(const B &\)'*: attempting to reference a deleted function**     範例 \(之前\)  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
     範例 \(之後\)  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
-   **靜態成員函式不支援 cv 限定詞。**  
  
     舊版 Visual C\+\+ 2015 允許靜態成員函式擁有 cv 限定詞。 此行為起因於 Visual C\+\+ 2015 與 Visual C\+\+ 2015 Update 1 的迴歸；Visual C\+\+ 2013 與舊版 Visual C\+\+ 拒絕以此方式撰寫的程式碼。 Visual C\+\+ 2015 與 Visual C\+\+ 2015 Update 1 的行為不正確，且不符合 C\+\+ 標準。  Visual Studio 2015 Update 2 拒絕以此方式撰寫的程式碼，並會發出編譯器錯誤 C2511。  
  
 **錯誤 C2511：'void A::func\(void\) const': overloaded member function not found in 'A'**     範例 \(之前\)  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
     範例 \(之後\)  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
-   **WinRT 程式碼不允許列舉的向前宣告** \(只影響 \/ZW\)  
  
     為 Windows 執行階段 \(WinRT\) 編譯的程式碼不允許向前宣告 `enum` 型別，類似於使用 \/clr 編譯器參數為 .Net Framework 編譯 Managed C\+\+ 程式碼的情形。 此行為可確保一律得知列舉的大小，並能正確將其投影至 WinRT 型別系統。 編譯器拒絕以此方式撰寫的程式碼，且會發出編譯器錯誤 C2599 以及編譯器錯誤 C3197。  
  
 **錯誤 C2599：*'CustomEnum'*: the forward declaration of a WinRT enum is not allowed 錯誤 C3197：*'public'*: can only be used in definitions**     範例 \(之前\)  
  
    ```cpp  
    namespace A {  
      public enum class CustomEnum: int32;  // forward declaration; error C2599, error C3197  
    }  
  
    namespace A {  
      public enum class CustomEnum: int32  
      {  
        Value1  
      };  
    }  
  
    public ref class Component sealed  
    {  
    public:  
      CustomEnum f()  
      {  
        return CustomEnum::Value1;  
      }  
    };  
    ```  
  
     範例 \(之後\)  
  
    ```cpp  
  
              // forward declaration of CustomEnum removed  
  
    namespace A {  
      public enum class CustomEnum: int32  
      {  
        Value1  
      };  
    }  
  
    public ref class Component sealed  
    {  
    public:  
      CustomEnum f()  
      {  
        return CustomEnum::Value1;  
      }  
    };  
    ```  
  
-   **無法以內嵌方式宣告多載的非成員運算子 new 與運算子 delete** \(層級 1 \(\/ W1\) 預設為開啟\)  
  
     舊版編譯器不會在以內嵌方式宣告多載的非成員運算子 new 與運算子 delete 函式時發出警告。 以此方式撰寫的程式碼語式錯誤 \(不需要診斷\)，且可能因為 new 與 delete 運算子不相符 \(尤其在搭配調整大小後的解除配置使用時\)，而導致難以診斷的記憶體問題。   編譯器現在會發出編譯器警告 C4595，協助識別以此方式撰寫的程式碼。  
  
 **警告 C4595：*'operator new'*: non\-member operator new or delete functions may not be declared inline**     範例 \(之前\)  
  
    ```cpp  
  
              inline void* operator new(size_t sz)  // warning C4595  
    {  
      ...  
    }  
    ```  
  
     範例 \(之後\)  
  
    ```cpp  
  
              void* operator new(size_t sz)  // removed inline  
    {  
      ...  
    }  
    ```  
  
     可能需要先將運算子定義從標頭檔移出，再將其移入對應的原始程式檔，才能修正以此方式撰寫的程式碼。