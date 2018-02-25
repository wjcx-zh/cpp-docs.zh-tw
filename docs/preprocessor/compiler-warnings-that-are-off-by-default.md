---
title: "預設為關閉的編譯器警告 |Microsoft 文件"
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- warnings, compiler
- cl.exe compiler, setting options
ms.assetid: 69809cfb-a38a-4035-b154-283a61938df8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 619e2c517305246937ed7428eadbcf40be31fe5b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="compiler-warnings-that-are-off-by-default"></a>預設為關閉的編譯器警告

編譯器包含預設關閉的警告，因為大部分的開發人員不想要看到它們。 在某些情況下，它們代表樣式的選擇，或常見慣用語位於較舊的程式碼，或利用語言的 Microsoft 擴充功能。 在其他情況下，它們可以表示的區域的程式設計人員通常都會正確運作，可能會導致非預期或未定義的行為。 有些警告可能非常累贅程式庫標頭中。

您可以使用下列選項之一，以啟用這些警告：

- **#pragma 警告 (預設：** *warning_number* **)**  
   指定的警告 (*warning_number*) 會在其預設層級啟用。 警告的文件包含警告的預設層級。

- **#pragma warning(** *warning_level* **:** *warning_number* **)**  
   指定的警告 (*warning_number*) 指定的層級啟用 (*warning_level*)。

- [/Wall](../build/reference/compiler-option-warning-level.md)  
   **/ 牆**啟用都預設為關閉的所有警告。 如果您使用此選項時，您可以關閉個別的警告使用[/wd](../build/reference/compiler-option-warning-level.md)選項。

- [/w*lnnnn*](../build/reference/compiler-option-warning-level.md)  
   這可讓警告 *nnnn* 層級*l*。

根據預設，下列警告會關閉。

|||
|-|-|
|[C4061](../error-messages/compiler-warnings/compiler-warning-level-4-c4061.md) （層級 4）|列舉值 '*識別碼*'參數中的列舉'*列舉*' case 標籤並未明確處理|
|[C4062](../error-messages/compiler-warnings/compiler-warning-level-4-c4062.md) （層級 4）|列舉值 '*識別碼*'參數中的列舉'*列舉*' 未處理|
|C4191 (層級 3)|'*運算子*': 不安全的轉換，從'*type_of_expression*'to'*type_required*'|
|[C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) （層級 4）|'*識別碼*': 從'*type1*'to'*type2*'，資料可能遺失|
|[C4254](../error-messages/compiler-warnings/compiler-warning-level-4-c4254.md) （層級 4）|'*運算子*': 從'*type1*'to'*type2*'，資料可能遺失|
|[C4255](../error-messages/compiler-warnings/compiler-warning-level-4-c4255.md) （層級 4）|'*函式*': 未提供的函式原型： 轉換為 '(void)' 的' （）'|
|[C4263](../error-messages/compiler-warnings/compiler-warning-level-4-c4263.md) （層級 4）|'*函式*': 成員函式不會覆寫任何基底類別虛擬成員函式|
|[C4264](../error-messages/compiler-warnings/compiler-warning-level-1-c4264.md) （層級 1）|'*virtual_function*': 沒有覆寫的基底虛擬成員函式'*類別*'; 函式已隱藏|
|[C4265](../error-messages/compiler-warnings/compiler-warning-level-3-c4265.md) （層級 3）|'*類別*': 類別有虛擬函式，但不是虛擬解構函式|
|[C4266](../error-messages/compiler-warnings/compiler-warning-level-4-c4266.md) （層級 4）|'*函式*': 沒有覆寫的基底虛擬成員函式'*類型*'; 函式已隱藏|
|[C4287](../error-messages/compiler-warnings/compiler-warning-level-3-c4287.md) （層級 3）|'*運算子*': unsigned 和負常數不相符|
|[C4289](../error-messages/compiler-warnings/compiler-warning-level-4-c4289.md) （層級 4）|使用非標準擴充: '*var*': for 迴圈範圍外使用 for-loop 中所宣告的迴圈控制變數|
|[C4296](../error-messages/compiler-warnings/compiler-warning-level-4-c4296.md) （層級 4）|'*運算子*': 運算式永遠是 false|
|[C4339](../error-messages/compiler-warnings/compiler-warning-level-4-c4339.md) （層級 4）|'*類型*': 未定義的類型使用中偵測到 CLR 中繼資料-使用這個型別可能會導致執行階段例外狀況|
|[C4342](../error-messages/compiler-warnings/compiler-warning-level-1-c4342.md) （層級 1）|行為變更: '*函式*' 呼叫，但在舊版中被呼叫的是成員運算子|
|[C4350](../error-messages/compiler-warnings/compiler-warning-level-1-c4350.md) （層級 1）|行為變更: '*member1*'呼叫而不是'*member2*'|
|[C4355](../error-messages/compiler-warnings/compiler-warning-c4355.md)|'this' : 在基底成員初始設定式清單中使用|
|[C4365](../error-messages/compiler-warnings/compiler-warning-level-4-c4365.md) （層級 4）|'*動作*': 從'*type_1*'to'*type_2*'，signed/unsigned 不相符|
|C4370 （層級 3）|因為較佳的封裝，類別配置已從舊版的編譯器變更|
|[C4371](../error-messages/compiler-warnings/c4371.md) （層級 3）|'*classname*': 類別配置可能已從舊版編譯器因為的成員有更好的封裝'*成員*'|
|C4388 （層級 4）|帶正負號/不帶正負號不相符|
|[C4412](../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md) （層級 2）|'*函式*': 函式簽章含有類型'*類型*';C + + 物件是純程式碼之間傳遞的不安全與混合或原生|
|C4426 （層級 1）|包含標頭，可能是因為 #pragma optimize （） 之後變更的最佳化旗標|
|[C4435](../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md) （層級 4）|'*class1*': /vd2 底下的物件配置將因虛擬基底而變更'*class2*'|
|[C4437](../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md) （層級 4）|從虛擬基底 dynamic_cast '*class1*'to'*class2*' 某些內容中可能會失敗|
|C4444 （層級 3）|此內容未實作最上層的 '__unaligned'|
|C4464 （層級 4）|相對 include 路徑包含 '..'|
|C4472 （層級 1）|'*識別碼*' 是原生列舉： 新增存取規範 (private/public) 以便宣告 managed 的列舉|
|[C4514](../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md) （層級 4）|'*函式*': 已移除未參考的內嵌函式|
|[C4536](../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md) （層級 4）|'type name': 類型名稱超出中繼資料的限制 '*限制*' 字元|
|[C4545](../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md) （層級 1）|逗號之前的運算式判斷值為遺漏引數清單的函式|
|[C4546](../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md) （層級 1）|逗號之前的函式呼叫遺漏引數清單|
|[C4547](../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md) （層級 1）|'*運算子*': 運算子逗號之前無效; 必須是具有副作用的運算子|
|[C4548](../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md) （層級 1）|逗號之前的運算式無效; 必須是具有副作用的運算式|
|[C4549](../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md) （層級 1）|'*operator1*': 逗號之前的運算子無效; 您是否想'*operator2*' 嗎？|
|[C4555](../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md) （層級 1）|運算式無效; 必須是具有副作用的運算式|
|[C4557](../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md) （層級 3）|'__assume' 包含作用 '*效果*'|
|[C4571](../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md) （層級 4）|Visual c + + 7.1; 以來變更的告知性： catch 語意不再攔截結構化例外狀況 (SEH)|
|C4574 （層級 4）|'*識別碼*'定義為' 0': 您是否想要使用 ' #if*識別碼*'？|
|C4582 （層級 4）|'*類型*': 未隱含呼叫建構函式|
|C4583 （層級 4）|'*類型*': 未隱含呼叫解構函式|
|C4587 （層級 1）|'*anonymous_structure*': 行為變更： 不再隱含呼叫建構函式|
|C4588 （層級 1）|'*anonymous_structure*': 行為變更： 不再隱含呼叫解構函式|
|C4598 （層級 1 和層級 3）|' #include"*標頭*"': 標頭數目*數目*先行編譯標頭中不符合目前在該位置的編譯|
|C4599 （層級 3）|'*選項**路徑*': 命令列引數數目*數目*不符先行編譯標頭|
|C4605 （層級 1）|'/D*巨集*' 目前的命令列上指定，但未指定建置先行編譯標頭時|
|[C4619](../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md) （層級 3）|#pragma 警告： 沒有警告編號 '*數目*'|
|[C4623](../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md) （層級 4）|'derived class': 因為無法存取基底類別預設建構函式，所以無法產生預設建構函式|
|[C4625](../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md) （層級 4）|'derived class': 因為無法存取基底類別複製建構函式，所以無法產生複製建構函式|
|[C4626](../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md) （層級 4）|'derived class': 因為無法存取基底類別的指派運算子，所以無法產生指派運算子|
|[C4628](../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md) （層級 1）|不支援使用 -Ze 的雙拼詞。 字元順序 '*了雙拼詞*'沒有解譯為替代語彙基元'*char*'|
|[C4640](../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md) （層級 3）|'*執行個體*': 區域靜態物件的建構不是安全執行緒|
|C4647 （層級 3）|行為變更： __is_pod (*類型*) 在舊版中有不同的值|
|C4654 （層級 4）|先行編譯標頭包含放在之前的程式碼行都會被忽略。 程式碼加入先行編譯標頭。|
|[C4668](../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md) （層級 4）|'*符號*'未定義成前置處理器巨集，以 '0' 取代'*指示詞*'|
|[C4682](../error-messages/compiler-warnings/compiler-warning-level-4-c4682.md) （層級 4）|'*符號*': 沒有方向參數屬性指定，預設為 [in]|
|[C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md) （層級 3）|'*使用者定義型別*': 行為可能變更，在 UDT 傳回呼叫慣例|
|[C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) （層級 1）|'*函式*': 非私用成員簽章含有組件私用原生類型'*native_type*'|
|[C4710](../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md) （層級 4）|'*函式*': 未內嵌函式|
|[C4738](../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md) （層級 3）|在記憶體中儲存 32 位元浮點結果，可能會損失效能|
|[C4746](../error-messages/compiler-warnings/compiler-warning-c4746.md)|暫時性存取 '*運算式*' 受限於 /volatile:\<iso &#124; ms > 設定; 請考慮使用 __iso_volatile_load/store 內建函式|
|C4749 （層級 4）|有條件地支援： 套用至 non standard 配置類型的 offsetof '*類型*'|
|C4767 （層級 4）|區段名稱 '*符號*' 超過 8 個字元，將由連結器截斷|
|C4768 （層級 3）|就會忽略 __declspec 屬性之前連結規格|
|C4774 （層級 4）|'*字串*': 格式字串引數中必須要有*數目*不是字串常值|
|C4786 （層級 3）|'*符號*': 物件名稱被截斷成'*數目*' 的偵錯資訊中的字元|
|[C4820](../error-messages/compiler-warnings/compiler-warning-level-4-c4820.md) （層級 4）|'*位元組*'位元組填補已加建構後'*member_name*'|
|C4826 （層級 2）|從轉換 '*type1*'to'*type2*' 是帶正負號擴充。 這可能導致意外發生執行階段行為。|
|C4837 （層級 4）|偵測到的三併詞: '？*字元*'取代'*字元*'|
|C4841 （層級 4）|使用非標準擴充： 複合成員指示項用於 offsetof|
|C4842 （層級 4）|'offsetof' 套用至使用多重繼承類型的結果不保證編譯器版本之間保持一致|
|[C4868](../error-messages/compiler-warnings/compiler-warning-c4868.md) （層級 4）|'_檔案_(*line_number*)' 編譯器不會強制執行括號初始設定清單中的左到右評估順序|
|[C4905](../error-messages/compiler-warnings/compiler-warning-level-1-c4905.md) （層級 1）|寬字串常值轉換成 'LPSTR'|
|[C4906](../error-messages/compiler-warnings/compiler-warning-level-1-c4906.md) （層級 1）|字串常值轉換成 'LPWSTR'|
|[C4917](../error-messages/compiler-warnings/compiler-warning-level-1-c4917.md) （層級 1）|'*宣告子*': GUID 僅能與類別、 介面或命名空間相關聯|
|[C4928](../error-messages/compiler-warnings/compiler-warning-level-1-c4928.md) （層級 1）|不合法的 copy-initialization; 已經隱含套用一個以上的使用者定義的轉換|
|[C4931](../error-messages/compiler-warnings/compiler-warning-level-4-c4931.md) （層級 4）|我們假設已針對 number 位元指標建置類型程式庫|
|[C4946](../error-messages/compiler-warnings/compiler-warning-level-1-c4946.md) （層級 1）|相關類別之間使用的 reinterpret_cast: '*class1*'和'*class2*'|
|C4962|'*函式*': 特性指引最佳化已停用，因為最佳化導致分析資料變成不一致|
|[C4986](../error-messages/compiler-warnings/compiler-warning-c4986.md) （層級 4）|'*符號*': 例外狀況規格與上一個宣告不符|
|C4987 （層級 4）|使用非標準的擴充：'throw (...)'|
|C4988 （層級 4）|'*符號*': 變數宣告為類別/函式範圍外|
|C5022|'*類型*': 多個移動建構函式指定|
|C5023|'*類型*': 指定多個 move 指派運算子|
|C5024 （層級 4）|'*類型*': move 建構函式已隱含定義為已刪除|
|C5025 （層級 4）|'*類型*': move 指派運算子已隱含定義為已刪除|
|C5026 （層級 1 和層級 4）|'*類型*': move 建構函式已隱含定義為已刪除|
|C5027 （層級 1 和層級 4）|'*類型*': move 指派運算子已隱含定義為已刪除|
|C5029 （層級 4）|使用非標準擴充： c + + 中的對齊屬性的變數、 資料成員及標記類型只適用於|
|C5031 （層級 4）|#pragma warning （pop): 可能不相符，快顯警告狀態推入不同的檔案|
|C5032 （層級 4）|偵測到任何對應 「 #pragma warning （pop 的) #pragma warning|
|C5035|使用功能 '*功能*' 函式會導致*函式*編譯為客體程式碼|
|C5036 （層級 1）|varargs 函式的指標轉換時使用 /hybrid:x86arm64 編譯 '*type1*'to'*type2*'|
|[C5038](../error-messages/compiler-warnings/c5038.md)|資料成員 '*member1*'將初始化資料成員之後'*member2*'|

除非已關閉這些警告[/ 寬鬆-](../build/reference/permissive-standards-conformance.md)編譯器選項設定：

|||
|-|-|
|[C4471 （層級 4）](../error-messages/compiler-warnings/compiler-warning-level-4-c4471.md)|不限範圍的列舉之向前宣告必須含有基礎類型 (假設是 int)|
|[C4608 （層級 3）](../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md)|'*union_member*'已經初始化的另一個等位的成員，在初始設定式清單中，'*union_member*'|

根據預設，在 Visual Studio 2015 之前的編譯器版本，這些警告已關閉：

|||
|-|-|
|[C4302](../error-messages/compiler-warnings/compiler-warning-level-2-c4302.md) （層級 2）|'*轉換*': 從截斷'*type1*'to'*type2*'|
|[C4311](../error-messages/compiler-warnings/compiler-warning-level-1-c4311.md) （層級 1）|'*變數*': 指標從截斷'*類型*'to'*類型*'|
|[C4312](../error-messages/compiler-warnings/compiler-warning-level-1-c4312.md) （層級 1）|'*作業*': 從'*type1*'to'*type2*' 更大的|
|[C4319](../error-messages/compiler-warnings/compiler-warning-level-1-c4319.md) （層級 1）|'*運算子*': 零擴充'*type1*'to'*type2*' 更大的|

根據預設，在 Visual Studio 2012 之前的編譯器版本，這些警告已關閉：

|||
|-|-|
|[C4431](../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md) （層級 4）|遺漏類型規範 - 假設為 int。 注意: C 已不再支援 default-int|

## <a name="see-also"></a>請參閱

[warning](../preprocessor/warning.md)
