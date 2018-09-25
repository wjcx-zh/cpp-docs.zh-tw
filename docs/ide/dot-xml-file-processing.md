---
title: .xml 檔案處理 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- XML documentation, processing XML file
ms.assetid: e70fdeae-80ac-4872-ab24-771c5635cfbf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f7cdbbe704e283177e4e3b4f0767db66e2e284e5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446312"
---
# <a name="xml-file-processing"></a>.XML 檔案處理

編譯器會針對程式碼中，標記為要產生文件的每個建構產生識別碼字串。 如需詳細資訊，請參閱[建議使用的文件註解標籤](../ide/recommended-tags-for-documentation-comments-visual-cpp.md)。 識別碼字串可唯一識別此建構。 處理 .xml 檔案的程式可以使用識別碼字串，來識別對應該識別碼且文件所適用的 .NET Framework 中繼資料/反映項目。

.xml 檔案不會以階層方式呈現您的程式碼，它是含有針對每個項目所產生之識別碼的一般清單。

編譯器在產生識別碼字串時會遵守下列規則：

- 字串中未放置任何空白字元。

- 識別碼字串的第一個部分會識別所識別的成員種類，格式為單一字元後面接著一個冒號。 使用的成員類型如下：

   |字元|描述|
   |---------------|-----------------|
   |N|namespace<br /><br /> 您無法將文件註解新增至命名空間，但可以使用命名空間的 cref 參考。|
   |T|型別︰類別、介面、建構、列舉、委派|
   |D|typedef|
   |F|Field - 欄位|
   |P|屬性 (包括索引子或其他索引屬性)|
   |M|方法 (包括像是建構函式、運算子之類的特殊方法)|
   |E|Event - 事件|
   |!|錯誤字串<br /><br /> 字串的其餘部分提供與錯誤相關的資訊。 Visual C++ 編譯器會針對無法解析的連結產生錯誤資訊。|

- 字串的第二個部分是項目的完整名稱 (從命名空間的根開始)。 項目名稱、其封入類型及命名空間會以句號來分隔。 如果項目名稱本身包含句點，則會以雜湊符號 ('#') 來取代它們。 假設沒有項目的名稱中直接含有雜湊符號。 例如，`String` 建構函式的完整名稱會是 "System.String.#ctor"。

- 針對屬性和方法，如果有方法的引數，則後面會接著以括弧括住的引數清單。 如果沒有任何引數，就不會出現括弧。 引數會以逗號分隔。 每個引數的編碼方式都會直接遵循它在 .NET Framework 簽章中的編碼方式：

   - 基底類型。 一般類型 (ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE) 會表示為類型的完整名稱。

   - 內建類型 (例如，ELEMENT_TYPE_I4、ELEMENT_TYPE_OBJECT、ELEMENT_TYPE_STRING、ELEMENT_TYPE_TYPEDBYREF 和 ELEMENT_TYPE_VOID) 會表示為對應之完整類型的完整名稱，例如 **System.Int32** 或 **System.TypedReference**。

   - ELEMENT_TYPE_PTR 會表示為 '*'，緊接在已修改的類型之後。

   - ELEMENT_TYPE_BYREF 會表示為 '\@'，緊接在已修改的類型之後。

   - ELEMENT_TYPE_PINNED 會表示為 '^'，緊接在已修改的類型之後。 Visual C++ 編譯器永遠不會產生這個。

   - ELEMENT_TYPE_CMOD_REQ 會表示為 '&#124;' 和修飾詞類別的完整名稱，緊接在已修改的類型之後。 Visual C++ 編譯器永遠不會產生這個。

   - ELEMENT_TYPE_CMOD_OPT 會表示為 '!' 和修飾詞類別的完整名稱，緊接在已修改的類型之後。

   - ELEMENT_TYPE_SZARRAY 會表示為 "[]"，緊接在陣列的元素類型之後。

   - ELEMENT_TYPE_GENERICARRAY 會表示為 "[?]"，緊接在陣列的元素類型之後。 Visual C++ 編譯器永遠不會產生這個。

   - ELEMENT_TYPE_ARRAY 會表示為 [*lowerbound*:`size`,*lowerbound*:`size`]，其中逗號數目的順位是 -1，而每個維度的下限和大小 (如果已知) 會以十進位格式表示。 如果未指定下限或大小，就會加以省略。 如果省略了特定維度的下限和大小，也會省略 ':'。 例如，下限為 1 且未指定大小的 2 維度陣列是 [1:,1:]。

   - ELEMENT_TYPE_FNPTR 會表示為 "=FUNC:`type`(*signature*)"，其中 `type` 是傳回類型，而 *signature* 是方法的引數。 如果沒有任何引數，就會省略括弧。 Visual C++ 編譯器永遠不會產生這個。

   下列簽章元件不會出現，因為絕對不會使用它們來區別多載方法：

   - 呼叫慣例

   - 傳回類型

   - ELEMENT_TYPE_SENTINEL

- 僅針對轉換運算子，此方法的傳回值會編碼為 ' ~'，後面接著傳回型別，如之前的編碼所示。

- 針對泛型類型，類型的名稱後面將接著反引號，然後是表示泛型類型參數數目的數字。  例如，套用至物件的

    ```xml
    <member name="T:MyClass`2">
    ```

   針對定義為 `public class MyClass<T, U>` 的類型。

   針對接受泛型型別作為參數的方法，會將泛型型別參數指定為前面加上反引號的數字 (例如 \`0、\`1)。  每個數字都表示類型泛型參數之以零為起始的陣列標記法。

## <a name="example"></a>範例

下列範例顯示針對類別及其成員產生識別碼字串的方式。

```cpp
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

## <a name="see-also"></a>請參閱

[XML 文件](../ide/xml-documentation-visual-cpp.md)