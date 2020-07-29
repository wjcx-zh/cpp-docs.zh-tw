---
title: 快速參考 (C++/CX)
ms.date: 12/30/2016
ms.assetid: ba457195-26e5-43aa-b99d-24a871e550f4
ms.openlocfilehash: 6effcaec6a619bdd674dcae3bf4092fe82404d08
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214967"
---
# <a name="quick-reference-ccx"></a>快速參考 (C++/CX)

Windows 執行階段支援僅在可信任的作業系統環境中執行的通用 Windows 平臺（UWP）應用程式、使用已授權的函式、資料類型和裝置，並透過 Microsoft Store 散發。 C + +/CX 簡化了 Windows 執行階段的應用程式撰寫。 本文是快速參考;如需更完整的檔，請參閱[類型系統](../cppcx/type-system-c-cx.md)。

當您在命令列上建立時，請使用 **/ZW**編譯器選項來建立 UWP 應用程式或 Windows 執行階段元件。 若要存取 Windows 執行階段中繼資料（winmd）檔案中所定義的 Windows 執行階段宣告，請指定指示詞 `#using` 或 **/FU**編譯器選項。 當您建立 UWP 應用程式的專案時，Visual Studio 預設會設定這些選項，並新增所有 Windows 執行階段程式庫的參考。

## <a name="quick-reference"></a>快速參考

|概念|標準 C++|C++/CX|備註|
|-------------|--------------------|------------------------------------------------------------------|-------------|
|基本類型|C++ 基本型別。|C + +/CX 基本類型，可執行在 Windows 執行階段中定義的基本類型。|`default`命名空間包含 c + +/cx 內建的基本類型。 編譯器會將 c + +/CX 基本類型隱含地對應至標準 c + + 類型。<br /><br /> `Platform`命名空間的系列包含的類型可實作為基礎 Windows 執行階段類型。|
||**`bool`**|**`bool`**|8 位元布林值。|
||**`wchar_t`**, **`char16_t`**|`char16`|表示 Unicode (UTF-16) 字碼指標的 16 位元非數值。|
||**`short`**<br /><br /> **`unsigned short`**|`int16`<br /><br /> `uint16`|16 位元帶正負號的整數。<br /><br /> 16 位元不帶正負號的整數。|
||**`int`**<br /><br /> **`unsigned int`**|**`int`**<br /><br /> `uint32`|32 位元帶正負號的整數。<br /><br /> 32 位元不帶正負號的整數。|
||**`long long`** 或**`__int64`**<br /><br /> **`unsigned long long`**|`int64`<br /><br /> `uint64`|64 位元帶正負號的整數。<br /><br /> 64 位元不帶正負號的整數。|
||**`float`**, **`double`**|`float32, float64`|32 位元或 64 位元 IEEE 754 浮點數。|
||**`enum`**|**`enum class`**<br /><br /> -或-<br /><br /> **`enum struct`**|32 位元列舉。|
||(不適用)|`Platform::Guid`|`Platform` 命名空間中的 128 位元非數值 (GUID)。|
||`std::time_get`|`Windows::Foundation::DateTime`|日期時間結構。|
||(不適用)|`Windows::Foundation::TimeSpan`|時間範圍結構。|
||(不適用)|`Platform::Object^`|Windows 執行階段型別系統之 c + + 視圖中的參考計數基底物件。|
||`std::wstring`<br /><br /> `L"..."`|`Platform::String^`|`Platform::String^` 是 Unicode 字元之參考計數且不可變的序列，可代表文字。|
|Pointer|物件指標 (`*`)：<br /><br /> `std::shared_ptr`|物件的控制代碼 (`^`，唸成 "hat")：<br /><br /> *T ^ 識別碼*|所有 Windows 執行階段類別都是使用控制碼對物件修飾詞來宣告。 物件的成員使用箭頭 (`->`) 類別成員存取運算子來存取。<br /><br /> Hat 修飾詞表示「會自動參考計數的 Windows 執行階段物件的指標」。 更明確地說，物件的控制代碼宣告編譯器應該插入程式碼，以自動管理物件的參考計數，而如果參考計數變成零，則刪除物件。|
|參考|物件的參考 (`&`)：<br /><br /> *T* `&` *識別碼*|追蹤參考 (`%`)：<br /><br /> *T* `%` *識別碼*|只有 Windows 執行階段的類型可以使用追蹤參考修飾詞來宣告。 物件的成員使用點 (`.`) 類別成員存取運算子來存取。<br /><br /> 追蹤參考表示「自動參考計數的 Windows 執行階段物件參考」。 更明確地說，追蹤參考宣告編譯器應該插入程式碼，以自動管理物件的參考計數，而如果參考計數變成零，則刪除物件。|
|動態類型宣告|`new`|`ref new`|配置 Windows 執行階段物件，然後傳回該物件的控制碼。|
|物件存留期管理|`delete`*識別碼*<br /><br /> `delete[]`  *標識*|(叫用解構函式。)|留存期是由參考計數決定。 呼叫 delete 會叫用解構函式，但本身不會釋放記憶體。|
|陣列宣告|*T 識別項* `[]`<br /><br /> `std::array`*識別碼*|`Array<` *T* `^>^` *識別項* `(` *大小* `)`<br /><br /> -或-<br /><br /> `WriteOnlyArray<` *T* `^>`  *識別項* `(` *大小* `)`|宣告型別 T^ 的一維可修改的或唯讀陣列。 陣列本身也是參考計數物件，必須使用物件的控制代碼修飾詞來宣告。<br /><br /> (陣列宣告使用 `Platform` 命名空間中的樣板標頭類別。)|
|類別宣告|**`class`***識別碼*`{}`<br /><br /> **`struct`***識別碼*`{}`|**`ref class`***識別碼*`{}`<br /><br /> **`ref struct`***識別碼*`{}`|宣告具有預設私用存取範圍的執行階段類別。<br /><br /> 宣告具有預設公用存取範圍的執行階段類別。|
|結構宣告|**`struct`***識別碼*`{}`<br /><br /> (亦即，一般舊資料結構 (POD))|**`value class`***識別碼*`{}`<br /><br /> **`value struct`***識別碼*`{}`|宣告具有預設私用存取範圍的 POD 結構。<br /><br /> 實值類別可以在 Windows 中繼資料中表示，但 Standard C++ 類別不可以。<br /><br /> 宣告具有預設公用存取範圍的 POD 結構。<br /><br /> 實值結構可以在 Windows 中繼資料中表示，但 Standard C++ 結構不可以。|
|介面宣告|只包含純虛擬函式的抽象類別。|**`interface class`***識別碼*`{}`<br /><br /> **`interface struct`***識別碼*`{}`|宣告具有預設私用存取範圍的介面。<br /><br /> 宣告具有預設公用存取範圍的介面。|
|代理人|`std::function`|`public delegate` *傳回類型* *delegate-type-identifier* `(` *[ parameters ]* `);`|宣告可以像函式呼叫一樣叫用的物件。|
|事件|(不適用)|**`event`***委派-類型識別碼**事件識別碼*`;`<br /><br /> *委派-類型識別碼**委派-識別碼*  =  `ref new` *委派-類型識別碼* `( this` *[，參數]*`);`<br /><br /> *event-identifier* `+=` *delegate-identifier* `;`<br /><br /> -或-<br /><br /> `EventRegistrationToken`*token-識別碼*  = *obj* `.`*事件識別碼* `+=`*委派-識別碼*`;`<br /><br /> -或-<br /><br /> **`auto`***token-識別碼*  = *obj*。*事件識別碼* `::add(`*委派-識別碼*`);`<br /><br /> *obj* `.` *event-identifier* `-=` *token-identifier* `;`<br /><br /> -或-<br /><br /> *obj* `.` *event-identifier* `::remove(` *token-identifier* `);`|宣告事件物件，此物件會儲存事件發生時所呼叫的事件處理常式 (委派) 集合。<br /><br /> 建立事件處理常式。<br /><br /> 加入事件處理常式。<br /><br /> 加入事件處理常式會傳回事件語彙基元 (*token-identifier*)。 如果您想要明確移除事件處理常式，您必須儲存事件語彙基元供以後使用。<br /><br /> 移除事件處理常式。<br /><br /> 若要移除事件處理常式，您必須指定您在加入事件處理常式時所儲存的事件語彙基元。|
|屬性|(不適用)|**`property`***T* *識別碼*;<br /><br /> **`property`***T* *識別碼* `[` *索引*`];`<br /><br /> **`property`***T* `default[` *索引*`];`|宣告存取類別或物件成員函式所使用的語法，與存取資料成員或索引陣列元素所使用的語法相同。<br /><br /> 宣告類別或物件成員函式的屬性。<br /><br /> 宣告物件成員函式的索引屬性。<br /><br /> 宣告類別成員函式的索引屬性。|
|參數化型別|範本|`generic <typename`*T* `> interface class` *識別碼*`{}`<br /><br /> `generic <typename` *T* `> delegate` *[return-type]* *delegate-identifier* `() {}`|宣告參數化介面類別。<br /><br /> 宣告參數化委派。|
|可為 Null 的實值型別|`boost::optional<T>`|[Platform：： IBox\<T>](../cppcx/platform-ibox-interface.md)|讓純量類型和值結構的變數具有的值 **`nullptr`** 。|

## <a name="see-also"></a>另請參閱

[C + +/CX 語言參考](../cppcx/visual-c-language-reference-c-cx.md)
