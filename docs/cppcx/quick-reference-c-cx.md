---
title: 快速參考 (C + + /CX) |Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: ba457195-26e5-43aa-b99d-24a871e550f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 272921d0a9ac00ec5ee69fb50a17a34e257b1725
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43692584"
---
# <a name="quick-reference-ccx"></a>快速參考 (C++/CX)
Windows 執行階段支援只能在值得信任的作業系統環境中執行，使用授權的函式、 資料類型及裝置，透過 Microsoft Store 散發的通用 Windows 平台 (UWP) 應用程式。 C + + /CX 簡化 Windows 執行階段撰寫的應用程式。 這篇文章是快速參考;如需更完整的文件，請參閱[型別系統](../cppcx/type-system-c-cx.md)。  
  
 當您建置命令列上時，使用 **/ZW**編譯器選項建置的 UWP 應用程式或 Windows 執行階段元件。 若要存取 Windows 執行階段宣告 Windows 執行階段中繼資料 (.winmd) 檔案中定義，指定`#using`指示詞或 **/FU**編譯器選項。 當您建立 UWP 應用程式的專案時，Visual Studio 預設會設定這些選項，並將所有的 Windows 執行階段程式庫的參考。  
  
## <a name="quick-reference"></a>快速參考  
  
|概念|標準 C++|C++/CX|備註|  
|-------------|--------------------|------------------------------------------------------------------|-------------|  
|基本類型|C++ 基本型別。|C + + /CX 中實作 Windows 執行階段中所定義的基本類型的基本類型。|`default`命名空間包含 C + + /CX 內建的基本類型。 編譯器會隱含地將對應 C + + /CX 標準 c + + 類型的基本類型。<br /><br /> `Platform`系列的命名空間包含實作基本的 Windows 執行階段類型的型別。|  
||`bool`|`bool`|8 位元布林值。|  
||`__wchar_t`|`char16`|表示 Unicode (UTF-16) 字碼指標的 16 位元非數值。|  
||`short`<br /><br /> `unsigned short`|`int16`<br /><br /> `uint16`|16 位元帶正負號的整數。<br /><br /> 16 位元不帶正負號的整數。|  
||`int`<br /><br /> `unsigned int`|`int`<br /><br /> `uint32`|32 位元帶正負號的整數。<br /><br /> 32 位元不帶正負號的整數。|  
||`long long` -或- `__int64`<br /><br /> `unsigned long long`|`int64`<br /><br /> `uint64`|64 位元帶正負號的整數。<br /><br /> 64 位元不帶正負號的整數。|  
||`float, double`|`float32, float64`|32 位元或 64 位元 IEEE 754 浮點數。|  
||`enum {}`|`enum class {}`<br /><br /> -或-<br /><br /> `enum struct {}`|32 位元列舉。|  
||(不適用)|`Platform::Guid`|`Platform` 命名空間中的 128 位元非數值 (GUID)。|  
||`std::time_get`|`Windows::Foundation::DateTime`|日期時間結構。|  
||(不適用)|`Windows::Foundation::TimeSpan`|時間範圍結構。|  
||(不適用)|`Platform::Object^`|參考計數基底物件的 Windows 執行階段類型系統的 c + + 檢視中。|  
||`std::wstring`<br /><br /> `L"..."`|`Platform::String^`|`Platform::String^` 是 Unicode 字元之參考計數且不可變的序列，可代表文字。|  
|Pointer|物件指標 (`*`)：<br /><br /> `std::shared_ptr`|物件的控制代碼 (`^`，唸成 "hat")：<br /><br /> *T^ identifier*|使用物件的控制代碼修飾詞來宣告所有的 Windows 執行階段類別。 物件的成員使用箭頭 (`->`) 類別成員存取運算子來存取。<br /><br /> Hat 修飾詞表示 Windows 執行階段物件會自動參考指標 counted 」。 更明確地說，物件的控制代碼宣告編譯器應該插入程式碼，以自動管理物件的參考計數，而如果參考計數變成零，則刪除物件。|  
|參考資料|物件的參考 (`&`)：<br /><br /> *T* `&` *識別項*|追蹤參考 (`%`)：<br /><br /> *T* `%` *識別項*|唯一的 Windows 執行階段類型可以宣告使用追蹤參考修飾詞。 物件的成員使用點 (`.`) 類別成員存取運算子來存取。<br /><br /> 追蹤參考表示 「 Windows 執行階段物件會自動計算參考的參考 」。 更明確地說，追蹤參考宣告編譯器應該插入程式碼，以自動管理物件的參考計數，而如果參考計數變成零，則刪除物件。|  
|動態類型宣告|`new`|`ref new`|配置的 Windows 執行階段物件，然後傳回該物件的控制代碼。|  
|物件存留期管理|`delete` *識別項*<br /><br /> `delete[]`  *識別項*|(叫用解構函式。)|留存期是由參考計數決定。 呼叫 delete 會叫用解構函式，但本身不會釋放記憶體。|  
|陣列宣告|*T 識別項* `[]`<br /><br /> `std::array` *識別項*|`Array<` *T* `^>^` *識別項* `(` *大小* `)`<br /><br /> -或-<br /><br /> `WriteOnlyArray<` *T* `^>`  *識別項* `(` *大小* `)`|宣告型別 T^ 的一維可修改的或唯讀陣列。 陣列本身也是參考計數物件，必須使用物件的控制代碼修飾詞來宣告。<br /><br /> (陣列宣告使用 `Platform` 命名空間中的樣板標頭類別。)|  
|類別宣告|`class`  *識別項* `{}`<br /><br /> `struct` *識別項* `{}`|`ref class` *識別項* `{}`<br /><br /> `ref struct` *識別項* `{}`|宣告具有預設私用存取範圍的執行階段類別。<br /><br /> 宣告具有預設公用存取範圍的執行階段類別。|  
|結構宣告|`struct` *識別項* `{}`<br /><br /> (亦即，一般舊資料結構 (POD))|`value class` *識別項* `{}`<br /><br /> `value struct` *識別項* `{}`|宣告具有預設私用存取範圍的 POD 結構。<br /><br /> 實值類別可以在 Windows 中繼資料中表示，但 Standard C++ 類別不可以。<br /><br /> 宣告具有預設公用存取範圍的 POD 結構。<br /><br /> 實值結構可以在 Windows 中繼資料中表示，但 Standard C++ 結構不可以。|  
|介面宣告|只包含純虛擬函式的抽象類別。|`interface class` *識別項* `{}`<br /><br /> `interface struct` *識別項* `{}`|宣告具有預設私用存取範圍的介面。<br /><br /> 宣告具有預設公用存取範圍的介面。|  
|Delegate - 委派|`std::function`|`public delegate` *傳回類型* *delegate-type-identifier* `(` *[ parameters ]* `);`|宣告可以像函式呼叫一樣叫用的物件。|  
|Event - 事件|(不適用)|`event` *delegate-type-identifier* *event-identifier* `;`<br /><br /> *delegate-type-identifier* *delegate-identifier* = `ref new`*delegate-type-identifier*`( this`*[, parameters]*`);`<br /><br /> *event-identifier* `+=` *delegate-identifier* `;`<br /><br /> -或-<br /><br /> `EventRegistrationToken` *token-identifier* = *obj*`.`*event-identifier*`+=`*delegate-identifier*`;`<br /><br /> -或-<br /><br /> `auto` *語彙基元識別項* = *obj*。*的事件識別項*`::add(`*委派識別碼*`);`<br /><br /> *obj* `.` *event-identifier* `-=` *token-identifier* `;`<br /><br /> -或-<br /><br /> *obj* `.` *event-identifier* `::remove(` *token-identifier* `);`|宣告事件物件，此物件會儲存事件發生時所呼叫的事件處理常式 (委派) 集合。<br /><br /> 建立事件處理常式。<br /><br /> 加入事件處理常式。<br /><br /> 加入事件處理常式會傳回事件語彙基元 (*token-identifier*)。 如果您想要明確移除事件處理常式，您必須儲存事件語彙基元供以後使用。<br /><br /> 移除事件處理常式。<br /><br /> 若要移除事件處理常式，您必須指定您在加入事件處理常式時所儲存的事件語彙基元。|  
|屬性|(不適用)|`property` *T* *識別項*;<br /><br /> `property` *T* *識別項* `[` *索引* `];`<br /><br /> `property` *T* `default[` *索引* `];`|宣告存取類別或物件成員函式所使用的語法，與存取資料成員或索引陣列元素所使用的語法相同。<br /><br /> 宣告類別或物件成員函式的屬性。<br /><br /> 宣告物件成員函式的索引屬性。<br /><br /> 宣告類別成員函式的索引屬性。|  
|參數化型別|範本|`generic <typename` *T* `> interface class` *識別項* `{}`<br /><br /> `generic <typename` *T* `> delegate` *[return-type]* *delegate-identifier* `() {}`|宣告參數化介面類別。<br /><br /> 宣告參數化委派。|  
|可為 Null 的實值型別|`boost::optional<T>`|[Platform:: ibox \<T >](../cppcx/platform-ibox-interface.md)|讓具有純量類型和值結構的變數能有 `nullptr`這個值。|  
  
## <a name="see-also"></a>另請參閱  
 [Visual c + + 語言參考](../cppcx/visual-c-language-reference-c-cx.md)