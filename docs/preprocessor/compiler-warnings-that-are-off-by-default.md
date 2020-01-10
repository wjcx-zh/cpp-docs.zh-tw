---
title: 預設為關閉的編譯器警告
ms.date: 08/29/2019
helpviewer_keywords:
- warnings, compiler
- cl.exe compiler, setting options
ms.assetid: 69809cfb-a38a-4035-b154-283a61938df8
ms.openlocfilehash: f74c413a81a1da6398666a0c15936cb76b5a7144
ms.sourcegitcommit: a361362354f6ce51eda4ffdb016b81c24cd225cb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71712666"
---
# <a name="compiler-warnings-that-are-off-by-default"></a>預設為關閉的編譯器警告

編譯器支援預設會關閉的警告，因為大部分的開發人員都找不到它們很有用。 在某些情況下，他們會警告有關樣式的選擇，或較舊程式碼中常見的慣用語。 其他警告則是關於使用語言的 Microsoft 擴充功能。 某些警告表示程式設計人員通常會做出不正確的假設，這可能會導致非預期或未定義的行為。 如果所有這些警告都已啟用，其中有些可能會在程式庫標頭中出現多次。 C 執行時間程式庫和C++標準程式庫的目的，只是在警告層級[/W4](../build/reference/compiler-option-warning-level.md)時，才會發出任何警告。

## <a name="enable-warnings-that-are-off-by-default"></a>啟用預設為關閉的警告

您可以使用下列其中一個選項，啟用通常預設為關閉的警告：

- **#pragma warning(default :** *warning_number* **)**

   指定的警告（*warning_number*）會在其預設層級啟用。 警告的文件包含警告的預設層級。

- **#pragma warning(** *warning_level* **:** *warning_number* **)**

   指定的警告（*warning_number*）已在指定的層級（*warning_level*）啟用。

- [/Wall](../build/reference/compiler-option-warning-level.md)

   `/Wall` 會啟用所有預設停用的警告。 如果您使用此選項，您可以使用[/wd](../build/reference/compiler-option-warning-level.md)選項來關閉個別的警告。

- [/w*Lnnnn*](../build/reference/compiler-option-warning-level.md)

   此選項會在層級*L*啟用警告*nnnn* 。

## <a name="warnings-that-are-off-by-default"></a>預設為關閉的警告

在 Visual Studio 2015 和更新版本中，預設會關閉下列警告：

|||
|-|-|
|[C4061](../error-messages/compiler-warnings/compiler-warning-level-4-c4061.md)（層級4）|case 標籤未明確處理列舉 '*enumeration*' 的參數中的列舉值 '*identifier*'|
|[C4062](../error-messages/compiler-warnings/compiler-warning-level-4-c4062.md)（層級4）|未處理列舉 '*enumeration*' 的參數中的枚舉器 '*identifier*'|
| [C4165](../error-messages/compiler-warnings/compiler-warning-level-1-c4165.md)（層級1） | ' HRESULT ' 正在轉換成 ' bool ';您確定這是您想要的嗎？ |
| [C4191](../error-messages/compiler-warnings/compiler-warning-level-3-c4191.md)（層級3）|'*operator*'：不安全的從 '*type_of_expression*' 轉換為 '*type_required*'|
|[C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md)（層級4）|'*identifier*'：從 '*type1*' 轉換為 '*type2*'，資料可能遺失|
|[C4254](../error-messages/compiler-warnings/compiler-warning-level-4-c4254.md)（層級4）|'*operator*'：從 '*type1*' 轉換為 '*type2*'，資料可能遺失|
|[C4255](../error-messages/compiler-warnings/compiler-warning-level-4-c4255.md)（層級4）|'*function*'：未指定函數原型：將 ' （） ' 轉換為 ' （void） '|
|[C4263](../error-messages/compiler-warnings/compiler-warning-level-4-c4263.md)（層級4）|'*function*'：成員函式不會覆寫任何基類虛擬成員函式|
|[C4264](../error-messages/compiler-warnings/compiler-warning-level-1-c4264.md)（層級1）|'*virtual_function*'：基底 '*class*' 的虛擬成員函式沒有可用的覆寫;函式已隱藏|
|[C4265](../error-messages/compiler-warnings/compiler-warning-level-3-c4265.md)（層級3）|'*class*'：類別有虛擬函式，但析構函數不是虛擬的|
|[C4266](../error-messages/compiler-warnings/compiler-warning-level-4-c4266.md)（層級4）|'*function*'：基底 '*type*' 的虛擬成員函式沒有可用的覆寫;函式已隱藏|
|[C4287](../error-messages/compiler-warnings/compiler-warning-level-3-c4287.md)（層級3）|'*operator*'：不帶正負號/負常數不相符|
|[C4289](../error-messages/compiler-warnings/compiler-warning-level-4-c4289.md)（層級4）|使用非標準的擴充： '*var*'： for 迴圈中宣告的迴圈控制變數會在 for 迴圈範圍外使用|
|[C4296](../error-messages/compiler-warnings/compiler-warning-level-4-c4296.md)（層級4）|'*operator*'：運算式一律為 false|
|[C4339](../error-messages/compiler-warnings/compiler-warning-level-4-c4339.md)（層級4）|'*type*'：在 CLR 中繼資料中偵測到使用未定義的類型-使用此類型可能會導致執行時間例外狀況|
|[C4342](../error-messages/compiler-warnings/compiler-warning-level-1-c4342.md)（層級1）|行為變更：呼叫了 '*function*'，但在先前的版本中呼叫了成員運算子|
|[C4350](../error-messages/compiler-warnings/compiler-warning-level-1-c4350.md)（層級1）|行為變更：呼叫了 '*member1*'，而非 '*member2*'|
|[C4355](../error-messages/compiler-warnings/compiler-warning-c4355.md)|'this' : 在基底成員初始設定式清單中使用|
|[C4365](../error-messages/compiler-warnings/compiler-warning-level-4-c4365.md)（層級4）|'*action*'：從 '*type_1*' 轉換為 '*type_2*'、已簽署/不帶正負號的不相符|
|C4370 （層級3）|因為較佳的封裝，類別配置已從舊版的編譯器變更|
|[C4371](../error-messages/compiler-warnings/c4371.md)（層級3）|'*classname*'：因為成員「*成員*」的封裝較佳，所以類別的版面配置可能已從舊版的編譯器變更|
|C4388 （層級4）|帶正負號/不帶正負號不相符|
|[C4412](../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md)（層級2）|'*function*'：函數簽名碼包含類型 '*type*';C++物件在純程式碼與混合或原生之間傳遞不安全|
|C4426 （層級1）|優化旗標在包含標頭之後已變更，可能是因為 #pragma optimize （） <sup>14.1</sup>|
|[C4435](../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md)（層級4）|'*class1*'：/Vd2 下的物件配置會因為虛擬基底 '*class2*' 而變更|
|[C4437](../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)（層級4）|從虛擬基底 '*class1*' 到 '*class2*' 的 dynamic_cast 在某些內容中可能會失敗|
|C4444 （層級3）|此內容未實作最上層的 '__unaligned'|
|[C4464](../error-messages/compiler-warnings/c4464.md)（層級4）|相對包含路徑包含 '： '|
|[C4471](../error-messages/compiler-warnings/compiler-warning-level-4-c4471.md)（層級4）|不限範圍列舉的向前宣告必須有基礎類型（假設為 int）<sup>永久</sup>|
|C4472 （層級1）|'*identifier*' 是原生列舉：新增存取規範（私用/公用）以宣告受控列舉|
|[C4514](../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md)（層級4）|'*function*'：已移除未參考的內嵌函數|
|[C4536](../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md)（層級4）|' type name '：類型名稱超出中繼資料 '*limit*' 個字元的限制|
|[C4545](../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md)（層級1）|逗號之前的運算式判斷值為遺漏引數清單的函式|
|[C4546](../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md)（層級1）|逗號之前的函式呼叫遺漏引數清單|
|[C4547](../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md)（層級1）|'*operator*'：逗號之前的運算子不會有任何作用;具有副作用的預期運算子|
|[C4548](../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md)（層級1）|逗號之前的運算式無效; 必須是具有副作用的運算式|
|[C4549](../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md)（層級1）|'*operator1*'：逗號之前的運算子不會有任何作用;您想要「*operator2*」嗎？|
|[C4555](../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md)（層級1）|運算式無效; 必須是具有副作用的運算式|
|[C4557](../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md)（層級3）|' __assume ' 包含效果 '*effect*'|
|[C4571](../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md)（層級4）|資訊： catch （...）自 Visual C++ 7.1 後已變更的語法;已不再攔截結構化例外狀況（SEH）|
|C4574 （層級4）|'*identifier*' 已定義為 ' 0 '：您是指使用 ' #if *identifier*' 嗎？|
|C4577 （層級1）|使用了 ' noexcept '，但未指定例外狀況處理模式;不保證例外狀況的終止。 指定/EHsc|
|C4582 （層級4）|'*type*'：未隱含呼叫此函式|
|C4583 （層級4）|'*type*'：未隱含呼叫析構函式|
|C4587 （層級1）|'*anonymous_structure*'：行為變更：不再隱含呼叫此函式|
|C4588 （層級1）|'*anonymous_structure*'：行為變更：不再隱含呼叫析構函式|
|[C4596](../error-messages/compiler-warnings/c4596.md)（層級4）|'*identifier*'：成員宣告<sup>14.3</sup> <sup>永久</sup>中有不合法的限定名稱|
|C4598 （層級1和層級3）|' #include "*標頭*" '：在先行編譯頭*檔中的*標頭編號不符合目前的編譯位置<sup>14.3</sup>|
|至 c4599 （層級3）|'*選項* *路徑*': 命令列引數數目*號碼*不符合預先編譯的標頭<sup>14.3</sup>|
|C4605 （層級1）|在目前的命令列上指定了 '/d*宏*'，但在建立先行編譯標頭檔時未指定|
|[C4608](../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md)（層級3）|'*union_member*' 已由初始化運算式清單 '*union_member*'<sup>永久</sup>中的另一個聯集成員所初始化|
|[C4619](../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md)（層級3）|#pragma 警告：沒有警告編號 '*number*'|
|[C4623](../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md)（層級4）|'derived class': 因為無法存取基底類別預設建構函式，所以無法產生預設建構函式|
|[C4625](../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md)（層級4）|'derived class': 因為無法存取基底類別複製建構函式，所以無法產生複製建構函式|
|[C4626](../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md)（層級4）|'derived class': 因為無法存取基底類別的指派運算子，所以無法產生指派運算子|
|[C4628](../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md)（層級1）|不支援使用 -Ze 的雙拼詞。 字元順序 '*連*詞 ' 未解讀為 '*char*' 的替代 token|
|[C4640](../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md)（層級3）|'*instance*'：本機靜態物件的結構不是安全線程|
| C4643 （層級4） | 標準不允許命名空間 std 中的C++向前宣告 ' identifier '。 <sup>15.8</sup> |
|C4647 （層級3）|行為變更： __is_pod （*類型*）在舊版中具有不同的值|
|C4654 （層級4）|包含先行編譯標頭檔的程式碼會被忽略。 將程式碼加入先行編譯標頭檔。 <sup>14.1</sup>|
|[C4668](../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md)（層級4）|'*symbol*' 未定義為預處理器宏，*以 ' 0 ' 取代 ' 指示*詞 '|
|[C4682](../error-messages/compiler-warnings/compiler-warning-level-4-c4682.md)（層級4）|'*symbol*'：沒有指定方向參數屬性，預設為 [in]|
|[C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)（層級3）|'*使用者定義類型*'：行為的可能變更，UDT 傳回呼叫慣例中的變更|
|[C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)（層級1）|'*function*'：非私用成員的簽章包含元件私用原生類型 '*native_type*'|
|[C4710](../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md)（層級4）|'*function*'：未內嵌函式|
|[C4738](../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md)（層級3）|在記憶體中儲存 32 位元浮點結果，可能會損失效能|
|[C4746](../error-messages/compiler-warnings/compiler-warning-c4746.md)|「*運算式*」的變動性存取受限於/volatile： \<iso&#124;ms > 設定;考慮使用 __iso_volatile_load/store 內建函式|
|C4749 （層級4）|有條件地支援： offsetof 套用至非標準版面配置類型 '*type*'|
|C4767 （層級4）|區段名稱 '*symbol*' 長度超過8個字元，且連結器將截斷|
|C4768 （層級3）|忽略連結規格前的 __declspec 屬性|
|C4774 （層級4）|'*字串*'：引數編號中預期的格式字串不是字串常*值*|
|C4777 （層級4）|'*function*'：格式字串 '*string*' 需要類型 '*type1*' 的引數，但 variadic 引數*編號*具有類型 '*type2*'|
|C4786 （層級3）|'*symbol*'：物件名稱已被截斷為偵錯工具資訊中的 '*number*' 個字元|
| [C4800](../error-messages/compiler-warnings/compiler-warning-level-3-c4800.md)（層級4） | 從 '*type*' 隱含轉換為 bool。 可能的資訊遺失<sup>16.0</sup> |
|[C4820](../error-messages/compiler-warnings/compiler-warning-level-4-c4820.md)（層級4）|結構 '*member_name*' 之後加入的 '*bytes*' 位元組填補|
| [C4822](../error-messages/compiler-warnings/compiler-warning-level-1-c4822.md)（層級1） | '*member*'：區域類別成員函式沒有主體 |
|C4826 （層級2）|從 '*type1*' 到 '*type2*' 的轉換已進行正負號擴充。 這可能會導致非預期的執行時間行為。|
|C4837 （層級4）|偵測到三並詞： '？？*字元*' 已取代成 '*字元*'|
|C4841 （層級4）|使用的非標準擴充： offsetof 中使用的複合成員指示項|
|C4842 （層級4）|套用至使用多重繼承之類型的 ' offsetof ' 結果，在編譯器版本之間不保證一致|
|[C4868](../error-messages/compiler-warnings/compiler-warning-c4868.md)（層級4）|'_file_（*line_number*） ' 編譯器可能不會在括弧初始化清單中強制執行由左至右的評估順序|
|[C4905](../error-messages/compiler-warnings/compiler-warning-level-1-c4905.md)（層級1）|寬字串常值轉換成 'LPSTR'|
|[C4906](../error-messages/compiler-warnings/compiler-warning-level-1-c4906.md)（層級1）|字串常值轉換成 'LPWSTR'|
|[C4917](../error-messages/compiler-warnings/compiler-warning-level-1-c4917.md)（層級1）|'*宣告子 '：* GUID 只能與類別、介面或命名空間產生關聯|
|[C4928](../error-messages/compiler-warnings/compiler-warning-level-1-c4928.md)（層級1）|不合法的 copy-initialization; 已經隱含套用一個以上的使用者定義的轉換|
|[C4931](../error-messages/compiler-warnings/compiler-warning-level-4-c4931.md)（層級4）|我們假設已針對 number 位元指標建置類型程式庫|
|[C4946](../error-messages/compiler-warnings/compiler-warning-level-1-c4946.md)（層級1）|在相關類別之間使用的 reinterpret_cast： '*class1*' 和 '*class2*'|
|C4962|'*function*'：特性指引優化已停用，因為優化導致分析資料變成不一致|
|[C4986](../error-messages/compiler-warnings/compiler-warning-c4986.md)（層級4）|'*symbol*'：例外狀況規格與上一個宣告不符|
|C4987 （層級4）|使用非標準的擴充：'throw (...)'|
|C4988 （層級4）|'*symbol*'：變數已在類別/函式範圍外宣告|
|C5022|'*type*'：指定了多個移動的構造函式|
|C5023|'*type*'：指定了多個移動指派運算子|
|C5024 （層級4）|'*type*'： move 函數已隱含定義為 deleted|
|C5025 （層級4）|'*type*'：移動指派運算子已隱含定義為刪除|
|C5026 （層級1和層級4）|'*type*'： move 函數已隱含定義為 deleted|
|C5027 （層級1和層級4）|'*type*'：移動指派運算子已隱含定義為刪除|
|C5029 （層級4）|使用非標準的擴充：中C++的對齊屬性僅適用于變數、資料成員和標記類型|
|C5031 （層級4）|#pragma 警告（pop）：可能不相符，彈出的警告狀態已推送至不同的檔案<sup>14.1</sup>|
|C5032 （層級4）|偵測到 #pragma 警告（push），但沒有對應的 #pragma 警告（pop） <sup>14.1</sup>|
|C5034|使用內建的 '*內部*' 會使函*式函數名稱*編譯為來賓代碼<sup>15.3</sup>|
|C5035|使用功能「*功能*」會使函*式函式名稱*編譯為來賓代碼<sup>15.3</sup>|
|C5036 （層級1）|以/hybrid： x86arm64 '*type1*' 編譯為 '*type2*' <sup>15.3</sup>時的 varargs 函式指標轉換|
|[C5038](../error-messages/compiler-warnings/c5038.md)（層級4）|資料成員 '*member1*' 將會在資料成員 '*member2*' <sup>15.3</sup>之後初始化|
|C5039 （層級4）|'*function*'：可能擲回函式的指標或參考，而該函式會傳遞至-EHc 底下的 extern C 函數。 如果此函式擲回例外狀況，則可能會發生未定義的行為。 <sup>15.5</sup>|
|C5042 （層級3）|'*function*'：在區塊範圍中的函式宣告不能在 standard C++中指定為 ' inline ';移除 ' inline ' 規範<sup>15.5</sup>|
|[C5045](../error-messages/compiler-warnings/c5045.md)|如果/Qspectre 參數指定<sup>15.7</sup> ，編譯器會插入記憶體負載的 Spectre 緩和措施|

<sup>14.1</sup>從 Visual Studio 2015 Update 1 開始可取得此警告。 \
<sup>14.3</sup>從 Visual Studio 2015 Update 3 開始可取得此警告。 \
<sup>15.3</sup>從 Visual Studio 2017 15.3 版開始提供此警告。 \
<sup>15.5</sup>從 Visual Studio 2017 15.5 版開始提供此警告。 \
<sup>15.7</sup>從 Visual Studio 2017 15.7 版開始提供此警告。 \
<sup>15.8</sup>從 Visual Studio 2017 15.8 版開始提供此警告。 \
<sup>16.0</sup>從 VISUAL STUDIO 2019 RTM 開始可取得此警告。 \
<sup>永久</sup>除非已設定[/permissive-](../build/reference/permissive-standards-conformance.md)編譯器選項，否則此警告是關閉的。

## <a name="warnings-off-by-default-in-earlier-versions"></a>先前版本中的警告預設為關閉

在 Visual Studio 2015 之前，這些警告在編譯器版本中預設為關閉：

|||
|-|-|
|[C4302](../error-messages/compiler-warnings/compiler-warning-level-2-c4302.md)（層級2）|'*轉換*'：從 '*type1*' 截斷為 '*type2*'|
|[C4311](../error-messages/compiler-warnings/compiler-warning-level-1-c4311.md)（層級1）|'*variable*'：從 '*type*' 到 '*type*' 的指標截斷|
|[C4312](../error-messages/compiler-warnings/compiler-warning-level-1-c4312.md)（層級1）|'*operation*'：從 '*type1*' 轉換為較大的 '*type2*'|
|[C4319](../error-messages/compiler-warnings/compiler-warning-level-1-c4319.md)（層級1）|'*operator*'：零將 '*type1*' 延伸至較大的 '*type2*'|

在 Visual Studio 2012 之前，編譯器的版本中，預設會關閉此警告：

|||
|-|-|
|[C4431](../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md)（層級4）|遺漏類型規範 - 假設為 int。 注意：C 不再支援 default-int|

## <a name="see-also"></a>另請參閱

[warning](../preprocessor/warning.md)
