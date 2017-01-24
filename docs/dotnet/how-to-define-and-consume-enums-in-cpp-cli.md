---
title: "如何：在 C++/CLI 中定義和使用列舉 | Microsoft Docs"
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
  - "列舉類別，指定基礎類型"
ms.assetid: df8f2b91-b9d2-4fab-9be4-b1d58b8bc570
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：在 C++/CLI 中定義和使用列舉
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題將討論 C\+\+\/CLI 列舉。  
  
## 指定列舉的基礎型別  
 根據預設，列舉型別的基礎型別為 `int`。不過，您可以指定要簽署或 `int`、 `short`、 `long`、 `__int32`或 `__int64`不帶正負號的表單。您也可以使用 `char`。  
  
```  
// mcppv2_enum_3.cpp  
// compile with: /clr  
public enum class day_char : char {sun, mon, tue, wed, thu, fri, sat};  
  
int main() {  
   // fully qualified names, enumerator not injected into scope  
   day_char d = day_char::sun, e = day_char::mon;  
   System::Console::WriteLine(d);  
   char f = (char)d;  
   System::Console::WriteLine(f);  
   f = (char)e;  
   System::Console::WriteLine(f);  
   e = day_char::tue;  
   f = (char)e;  
   System::Console::WriteLine(f);  
}  
```  
  
 **Output**  
  
  **凱撒**  
**0**  
**1**  
**2**   
## 如何將 Managed 和標準列舉之間  
 不在列舉和整數類資料型別之間的標準轉換;需要轉型。  
  
```  
// mcppv2_enum_4.cpp  
// compile with: /clr  
enum class day {sun, mon, tue, wed, thu, fri, sat};  
enum {sun, mon, tue, wed, thu, fri, sat} day2; // unnamed std enum  
  
int main() {  
   day a = day::sun;  
   day2 = sun;  
   if ((int)a == day2)  
   // or...  
   // if (a == (day)day2)  
      System::Console::WriteLine("a and day2 are the same");  
   else  
      System::Console::WriteLine("a and day2 are not the same");  
}  
```  
  
 **Output**  
  
  **和 day2 相同**   
## 運算子和列舉  
 下列運算子適用於以 C\+\+\/CLI 的列舉:  
  
|運算子|  
|---------|  
|\=\= \!\= \< \> \<\= \>\=|  
|\+ \-|  
|&#124; ^ & ~|  
|\+\+ \-\-|  
|sizeof|  
  
 運算子&#124;^ & &#124; \+\+\-\-為列舉型別只能定義與整數基本型別，不包括 bool。兩個運算元必須是列舉型別。  
  
 編譯器無法將靜態或動態檢查列舉作業的結果;作業可能會造成值不是列舉的有效列舉值範圍內。  
  
> [!NOTE]
>  要在 Managed C\+\+\/CLI 的列舉類別相當不同的 C\+\+11 引入 enum 類別輸入 Unmanaged 程式碼。  特別是， C\+\+11 列舉類別型別不支援與 Managed 列舉類別輸入 C\+\+\/CLI 的運算子，因此， C\+\+\/CLI 原始程式碼必須提供 Managed 列舉類別宣告的存取範圍規範為了與 Unmanaged \(C\+\+11\) 列舉類別宣告區分它們。  如需列舉的詳細資訊，以 C\+\+\/CLI C\+\+\/CX 分類，因此， C\+\+11，請參閱 [enum class](../windows/enum-class-cpp-component-extensions.md)。  
  
```  
// mcppv2_enum_5.cpp  
// compile with: /clr  
private enum class E { a, b } e, mask;  
int main() {  
   if ( e & mask )   // C2451 no E->bool conversion  
      ;  
  
   if ( ( e & mask ) != 0 )   // C3063 no operator!= (E, int)  
      ;  
  
   if ( ( e & mask ) != E() )   // OK  
      ;  
}  
```  
  
```  
// mcppv2_enum_6.cpp  
// compile with: /clr  
private enum class day : int {sun, mon};  
enum : bool {sun = true, mon = false} day2;  
  
int main() {  
   day a = day::sun, b = day::mon;  
   day2 = sun;  
  
   System::Console::WriteLine(sizeof(a));  
   System::Console::WriteLine(sizeof(day2));  
   a++;  
   System::Console::WriteLine(a == b);  
}  
```  
  
 **Output**  
  
  **4**  
**1**  
**True**   
## 請參閱  
 [enum class](../windows/enum-class-cpp-component-extensions.md)