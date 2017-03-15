---
title: ".XML 檔案處理 | Microsoft Docs"
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
  - "XML 文件, 處理 XML 檔"
ms.assetid: e70fdeae-80ac-4872-ab24-771c5635cfbf
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# .XML 檔案處理
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

編譯器會為每一個加上標記的程式碼的建構產生一個 ID 字串，用來產生文件   如需詳細資訊，請參閱 [建議的標記文件註解](../ide/recommended-tags-for-documentation-comments-visual-cpp.md)。  ID 字串會將建構獨一無二地識別出來。  處理 .xml 檔案的程式可以使用 ID 字串來識別文件適用的 .NET Framework 中繼資料或反映項目。  
  
 .xml 檔案不是您的程式碼，其階層式表示與一個平面圖式的清單中每個項目的。  
  
 在產生 ID 字串時，編譯器會遵守下列的規則：  
  
-   字串中不能有空白。  
  
-   ID 字串的第一個部分 \(單一字元後接著一個分號\) 識別了成員的種類。  下面是使用的成員型別：  
  
    |字元|描述|  
    |--------|--------|  
    |N|namespace<br /><br /> 您不能將文件註解加入至命名空間，此命名空間的 cref 參考是可能的。|  
    |T|型別：類別、介面、結構、列舉、委派|  
    |D|typedef|  
    |F|欄位|  
    |P|屬性 \(包括索引工具或其他索引屬性\)|  
    |M|方法 \(包括如建構函式、運算子等特別的方法\)|  
    |E|事件|  
    |\!|錯誤字串<br /><br /> 字串的其餘部分會提供該錯誤的相關資訊。  Visual C\+\+ 編譯器產生無法解析的連結的錯誤資訊。|  
  
-   字串的第二個部分是該項目的完整名稱 \(開始於命名空間的根\)。  項目的名稱，其封入型別或型別和命名空間以句號分隔。  若該項目的名稱本身含有句號，則句號會被井字號 \(\#\) 所替換。  假設，項目具有雜湊標記直接在它的名稱。  例如， `String` 建構函式的完整名稱是「System.String.\#ctor」。  
  
-   對於屬性和方法，若方法有引數，則後面會接著由括號括起來的引數清單。  如果沒有引數，就不會有括弧出現。  引數間是以逗號來分隔。  每個引數的編碼直接遵照 .NET Framework 簽章中的編碼方式：  
  
    -   基底型別。  標準型別 \(ELEMENT\_TYPE\_CLASS 或 ELEMENT\_TYPE\_VALUETYPE\) 以該型別的完整名稱表示。  
  
    -   內建型別 \(例如，ELEMENT\_TYPE\_I4、ELEMENT\_TYPE\_OBJECT、ELEMENT\_TYPE\_STRING、ELEMENT\_TYPE\_TYPEDBYREF。  和 ELEMENT\_TYPE\_VOID\) 表示為對應的完整型別，例如，或者 **System.Int32System.TypedReference**的完整名稱。  
  
    -   ELEMENT\_TYPE\_PTR 於修改的型別後以 '\*' 表示。  
  
    -   ELEMENT\_TYPE\_BYREF 於修改的型別後以 '@' 表示。  
  
    -   ELEMENT\_TYPE\_PINNED 於修改的型別後以 '^' 表示。  Visual C\+\+ 編譯器永遠不會產生此。  
  
    -   ELEMENT\_TYPE\_CMOD\_REQ 於修改的型別後以 '&#124;' 和修飾詞類別的完整名稱表示。  Visual C\+\+ 編譯器永遠不會產生此。  
  
    -   ELEMENT\_TYPE\_CMOD\_OPT 於修改的型別後以 '\!' 和修飾詞類別的完整名稱表示。  
  
    -   ELEMENT\_TYPE\_SZARRAY 在陣列的項目型別後以 "\[\]" 表示。  
  
    -   ELEMENT\_TYPE\_GENERICARRAY 在陣列的項目型別後以 "\[?\]" 表示。  Visual C\+\+ 編譯器永遠不會產生此。  
  
    -   ELEMENT\_TYPE\_ARRAY 以 \[*lowerbound*:`size`，*lowerbound*:`size`\] 表示，其中逗號的數目為陣序規範 \-1，若已知每個維度的下限與大小，則以十進位表示。  若沒有指定下限或大小，則會被忽略。  若省略了特定維度的下限及大小，則 ":" 也會被省略。  例如，一個沒有指定大小的二維陣列的下限是 1，則會以 \[1:,1:\] 表示。  
  
    -   ELEMENT\_TYPE\_FNPTR 以「\=FUNC:`type`\(*signature*\)」表示，其中 `type` 為傳回型別，而 *signature* 為方法的引數。  如果沒有引數的話，就會省略括弧。  Visual C\+\+ 編譯器永遠不會產生此。  
  
     將不顯示下列的簽章元件，因為它們從不用來區分多載的方法。  
  
    -   呼叫慣例  
  
    -   傳回型別  
  
    -   ELEMENT\_TYPE\_SENTINEL  
  
-   只有轉換運算子，方法的傳回值會編碼成「&#124;」的傳回型別後面，先前輸入的。  
  
-   泛型型別的名稱後面會有一個反勾號，然後是表示泛型型別參數數目的數字。  例如：  
  
    ```  
    <member name="T:MyClass`2">  
    ```  
  
     定義為 `public class MyClass<T, U>`的型別。  
  
     若為使用泛型型別做為參數的方法，會將泛型型別參數指定為前面加上反勾號的數字 \(例如 \`0、\`1\)。  每個數字都代表型別泛型參數以零起始的陣列。  
  
## 範例  
 下列範例顯示類別的 ID 字串及其成員如何產生。  
  
```  
// xml_id_strings.cpp  
// compile with: /clr /doc /LD  
///   
namespace N {    
// "N:N"  
  
   /// <see cref="System" />  
   //  <see cref="N:System"/>  
   ref class X {      
   // "T:N.X"  
  
   protected:  
      ///   
      !X(){}     
      // "M:N.X.Finalize", destructor's representation in metadata  
  
   public:  
      ///   
      X() {}     
      // "M:N.X.#ctor"  
  
      ///   
      static X() {}     
      // "M:N.X.#cctor"  
  
      ///   
      X(int i) {}     
      // "M:N.X.#ctor(System.Int32)"  
  
      ///   
      ~X() {}     
      // "M:N.X.Dispose", Dispose function representation in metadata  
  
      ///   
      System::String^ q;     
      // "F:N.X.q"  
  
      ///   
      double PI;     
      // "F:N.X.PI"  
  
      ///   
      int f() { return 1; }     
      // "M:N.X.f"  
  
      ///   
      int bb(System::String ^ s, int % y, void * z) { return 1; }  
      // "M:N.X.bb(System.String,System.Int32@,System.Void*)"  
  
      ///   
      int gg(array<short> ^ array1, array< int, 2 >^ IntArray) { return 0; }   
      // "M:N.X.gg(System.Int16[], System.Int32[0:,0:])"  
  
      ///   
      static X^ operator+(X^ x, X^ xx) { return x; }  
     // "M:N.X.op_Addition(N.X,N.X)"  
  
      ///   
      property int prop;     
      // "M:N.X.prop"  
  
      ///   
      property int prop2 {     
      // "P:N.X.prop2"  
  
         ///   
         int get() { return 0; }  
         // M:N.X.get_prop2  
  
         ///   
         void set(int i) {}  
         // M:N.X.set_prop2(System.Int32)  
      }  
  
      ///   
      delegate void D(int i);   
      // "T:N.X.D"  
  
      ///   
      event D ^ d;   
      // "E:N.X.d"  
  
      ///   
      ref class Nested {};   
      // "T:N.X.Nested"  
  
      ///   
      static explicit operator System::Int32 (X x) { return 1; }   
      // "M:N.X.op_Explicit(N.X!System.Runtime.CompilerServices.IsByValue)~System.Int32"  
   };  
}  
```  
  
## 請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)