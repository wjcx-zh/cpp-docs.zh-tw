---
title: 編譯器警告 C4400 至 C4599
ms.date: 04/21/2019
f1_keywords:
- C4413
- C4415
- C4416
- C4417
- C4418
- C4419
- C4421
- C4423
- C4424
- C4425
- C4426
- C4427
- C4438
- C4442
- C4443
- C4444
- C4446
- C4447
- C4448
- C4449
- C4450
- C4452
- C4453
- C4454
- C4455
- C4472
- C4474
- C4475
- C4476
- C4478
- C4480
- C4482
- C4483
- C4491
- C4492
- C4493
- C4494
- C4495
- C4496
- C4497
- C4498
- C4499
- C4509
- C4519
- C4531
- C4542
- C4562
- C4568
- C4569
- C4573
- C4574
- C4575
- C4582
- C4583
- C4585
- C4586
- C4587
- C4588
- C4591
- C4592
- C4593
- C4594
- C4595
helpviewer_keywords:
- C4413
- C4415
- C4416
- C4417
- C4418
- C4419
- C4421
- C4423
- C4424
- C4425
- C4426
- C4427
- C4438
- C4442
- C4443
- C4444
- C4446
- C4447
- C4448
- C4449
- C4450
- C4451
- C4452
- C4453
- C4454
- C4455
- C4456
- C4457
- C4459
- C4472
- C4474
- C4475
- C4476
- C4478
- C4480
- C4482
- C4483
- C4491
- C4492
- C4493
- C4494
- C4495
- C4496
- C4497
- C4498
- C4499
- C4509
- C4519
- C4531
- C4542
- C4562
- C4568
- C4569
- C4573
- C4574
- C4575
- C4582
- C4583
- C4585
- C4586
- C4587
- C4588
- C4591
- C4592
- C4593
- C4594
- C4595
ms.assetid: b07850a5-ae89-48ea-bf9a-f0e30939f9b9
ms.openlocfilehash: d1a4da3d5e721c85879441a53ef4bc00549b587d
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230489"
---
# <a name="compiler-warnings-c4400-through-c4599"></a>編譯器警告 C4400 至 C4599

本檔的這一節中的文章說明編譯器所產生的警告訊息子集。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>警告訊息

|警告|訊息|
|-------------|-------------|
|[編譯器警告（層級1） C4600](compiler-warning-level-1-c4600.md)|#pragma '*宏名稱*'：必須是有效的非空白字串|
|[編譯器警告（層級4） C4400](../../error-messages/compiler-warnings/compiler-warning-level-4-c4400.md)|'*type*'：不支援此類型的 const/volatile 限定詞|
|[編譯器警告（層級1） C4401](../../error-messages/compiler-warnings/compiler-warning-level-1-c4401.md)|'*bit '：* 成員是位欄位|
|[編譯器警告（層級1） C4402](../../error-messages/compiler-warnings/compiler-warning-level-1-c4402.md)|必須使用 PTR 運算子|
|[編譯器警告（層級1） C4403](../../error-messages/compiler-warnings/compiler-warning-level-1-c4403.md)|不合法的 PTR 運算子|
|[編譯器警告（層級3） C4404](../../error-messages/compiler-warnings/compiler-warning-level-3-c4404.md)|已忽略指示詞上的句點|
|[編譯器警告（層級1） C4405](../../error-messages/compiler-warnings/compiler-warning-level-1-c4405.md)|'*identifier*'：識別碼是保留字|
|[編譯器警告（層級1） C4406](../../error-messages/compiler-warnings/compiler-warning-level-1-c4406.md)|已忽略指示詞上的運算元|
|[編譯器警告（層級1） C4407](../../error-messages/compiler-warnings/compiler-warning-level-1-c4407.md)|在成員表示的不同指標之間進行轉換時，編譯器可能會產生不正確的程式碼|
|[編譯器警告（層級4） C4408](../../error-messages/compiler-warnings/compiler-warning-level-4-c4408.md)|匿名「結構&#124;聯集」未宣告任何資料成員|
|[編譯器警告（層級1） C4409](../../error-messages/compiler-warnings/compiler-warning-level-1-c4409.md)|不正確指令大小|
|[編譯器警告（層級1） C4410](../../error-messages/compiler-warnings/compiler-warning-level-1-c4410.md)|運算元的大小不合法|
|[編譯器警告（層級1） C4411](../../error-messages/compiler-warnings/compiler-warning-level-1-c4411.md)|'*identifier*'：符號解析為置換 register|
|[編譯器警告（層級2） C4412](../../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md)|'*function*'：函數簽名碼包含類型 '*type*';C++物件在純程式碼與混合或原生之間傳遞不安全。|
|編譯器警告 C4413|' classname：： member '：參考成員已初始化為不會在函式結束後保存的暫存|
|[編譯器警告（層級3） C4414](../../error-messages/compiler-warnings/compiler-warning-level-3-c4414.md)|'*function*'：將函式轉換為 near 的短跳躍|
|編譯器警告（層級1） C4415|duplicate __declspec(code_seg('*name*'))|
|編譯器警告（層級1） C4416|__declspec （code_seg （...））包含空字串：已忽略|
|編譯器警告（層級1） C4417|明確的範本具現化不能有 __declspec （code_seg （...））：已忽略|
|編譯器警告（層級1） C4418|在列舉上忽略 __declspec （code_seg （...））|
|編譯器警告（層級3） C4419|套用至私用 ref 類別 '*class*' 時，'*symbol*' 不會有任何作用。|
|[編譯器警告（層級1） C4420](../../error-messages/compiler-warnings/compiler-warning-level-1-c4420.md)|'*checked_operator*'：無法使用運算子，請改用 '*operator*';執行時間檢查可能會受到危害|
|編譯器警告（層級3） C4421|'*parameter*'：可繼續函數上的參考參數可能不安全|
|編譯器警告（層級3） C4423|' std：： bad_alloc '：將由行*號*上的類別（'*type*'）攔截|
|編譯器警告（層級3） C4424|攔截 '*type1*'，其前面加上 '*type2*' （行*號*）;如果擲回 ' std：： bad_alloc '，可能會導致無法預期的行為|
|編譯器警告（層級1） C4425|SAL 注釋無法套用至 ' ... '|
|編譯器警告（層級1） C4426|優化旗標在包含標題之後變更，可能是因為 #pragma 優化（）|
|編譯器警告（層級1） C4427|'*operator*'：常數除法溢位，未定義的行為|
|[編譯器警告（層級4） C4429](../../error-messages/compiler-warnings/compiler-warning-level-4-c4429.md)|可能是不完整或格式不正確的通用字元名稱|
|[編譯器警告（錯誤） C4430](../../error-messages/compiler-warnings/compiler-warning-c4430.md)|遺漏類型規範 - 假設為 int。 注意：C++不支援 default-int|
|[編譯器警告（層級4） C4431](../../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md)|遺漏類型規範 - 假設為 int。 注意：C 不再支援 default-int|
|[編譯器警告（層級4） C4434](../../error-messages/compiler-warnings/compiler-warning-level-4-c4434.md)|靜態的函式必須具有私用存取範圍;變更為私用存取|
|[編譯器警告（層級4） C4435](../../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md)|'*derived_class*'：/Vd2 下的物件配置會因為虛擬基底 '*base_class*' 而變更|
|[編譯器警告（層級1） C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)|在\_函數或析構函式中，從虛擬基底 '*base_class*' 到 '*derived_class*' 的動態轉型可能會因部分結構化的物件而失敗|
|[編譯器警告（層級4） C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)|從\_虛擬基底 '*base_class*' 到 '*derived_class*' 的動態轉換在某些內容中可能會失敗|
|編譯器警告 C4438|'*function*'：無法在/await： clrcompat 模式中安全地呼叫。 如果 '*function*' 呼叫 clr，可能會導致 clr 標頭損毀|
|[編譯器警告（錯誤） C4439](../../error-messages/compiler-warnings/compiler-warning-c4439.md)|'*function*'：簽章中具有 managed 類型的函式定義必須有 __clrcall 呼叫慣例|
|[編譯器警告（層級1） C4440](../../error-messages/compiler-warnings/compiler-warning-level-1-c4440.md)|已忽略從 '*calling_convention1*' 到 '*calling_convenction2*' 呼叫慣例的重新定義|
|[編譯器警告（層級1） C4441](../../error-messages/compiler-warnings/compiler-warning-level-1-c4441.md)|已忽略 '*calling_convention1*' 的呼叫慣例;改為使用 '*calling_convention2*'|
|編譯器警告（層級1） C4442|__annotation 引數中的內嵌 null 結束字元。  值將會被截斷。|
|編譯器警告（層級1） C4443|pragma 參數必須是 ' 0 '、' 1 ' 或 ' 2 '|
|編譯器警告（層級3） C4444|'*identifier*'：最上層 ' __unaligned ' 未在此內容中執行|
|[編譯器警告（層級1） C4445](../../error-messages/compiler-warnings/compiler-warning-level-1-c4445.md)|'*function*'：在 ' WinRT&#124;managed ' 類型中，虛擬方法不可為私用|
|編譯器警告（層級1） C4446|'*type*'：因為與類型名稱衝突，所以無法將成員 '*name1*' 對應到這個類型。 方法已重新命名為 '*name2*'|
|編譯器警告（層級1） C4447|找不到執行緒模型的 ' main ' 簽章。 請考慮使用 ' int main （platform：：\<Array platform：： String ^ > ^ args） '。|
|編譯器警告 C4448|'*type*1 ' 沒有在中繼資料中指定的預設介面。 挑選： '*type2*'，可能會在執行時間失敗。|
|編譯器警告 C4449|'*type*' 未密封的類型應標記為 ' [WebHostHidden] '|
|編譯器警告 C4450|'*type1*' 應標記為 ' [WebHostHidden] '，因為它衍生自 '*type2*'|
|編譯器警告（層級4） C4451|' 類別名稱1>：： member '：在此內容中使用 ref 類別 ' 類別名稱2>：： member ' 可能會導致物件的封送處理不正確|
|編譯器警告（層級1） C4452|'*identifier*'：公用類型不能在全域範圍中。 它必須位於命名空間中，其為輸出 winmd 檔案名稱的子系。|
|編譯器警告（層級1） C4453|'*type*'：' [WebHostHidden] ' 類型不能用在非 ' [WebHostHidden] ' 之公用類型的已發行介面上|
|編譯器警告（層級1） C4454|'*function*' 多載了輸入參數數目，但未指定 [DefaultOverload]。 挑選 '*宣告 ' 做*為預設多載|
|編譯器警告（層級1） C4455|' operator *operator*'：保留不是以底線開頭的常值尾碼識別碼|
|[編譯器警告 (層級 4) C4456](compiler-warning-level-4-c4456.md)|'*identifier*' 的宣告會隱藏先前的區域宣告|
|[編譯器警告 (層級 4) C4457](compiler-warning-level-4-c4457.md)|'*identifier*' 的宣告會隱藏函式參數|
|[編譯器警告 (層級 4) C4458](compiler-warning-level-4-c4458.md)|'*identifier*' 的宣告會隱藏類別成員|
|[編譯器警告（層級4） C4459](compiler-warning-level-4-c4459.md)|'*identifier*' 的宣告會隱藏全域宣告|
|[編譯器警告（層級4） C4460](../../error-messages/compiler-warnings/compiler-warning-level-4-c4460.md)|' WinRT&#124;managed ' 運算子 '*運算子*' 具有以傳址方式傳遞的參數。 ' WinRT&#124;managed '*運算子 ' 運算子 ' 與* C++運算子 '*cpp_operator*' 有不同的語義，您打算以傳值方式傳遞嗎？|
|[編譯器警告（層級1） C4461](../../error-messages/compiler-warnings/compiler-warning-level-1-c4461.md)|'*classname*'：此類別具有完成項 '！完成項 ' 但沒有任何析構函*式 ' ~* *dtor*'|
|[編譯器警告（層級1，錯誤） C4462](../../error-messages/compiler-warnings/compiler-warning-level-1-c4462.md)|'*type*'：無法判斷類型的 GUID。 程式可能在執行階段失敗。|
|[編譯器警告（層級4） C4463](compiler-warning-level-4-c4463.md)|溢出將 '*value*' 指派給位欄位，其只能保存 '*min_value*' 到 '*max_value*' 的值|
|[編譯器警告 (層級 4) C4464](../../error-messages/compiler-warnings/c4464.md)|相對包含路徑包含 '： '|
|[編譯器警告（層級1） C4470](../../error-messages/compiler-warnings/compiler-warning-level-1-c4470.md)|已忽略/clr 下的浮點控制 pragma|
|[編譯器警告（層級4） C4471](compiler-warning-level-4-c4471.md)|'*列舉*'：不限範圍列舉的向前宣告必須有基礎類型（假設為 int）|
|編譯器警告（層級1） C4472|'*identifier*' 是原生列舉：新增存取規範（私用/公用）以宣告 ' WinRT&#124;管理 ' 列舉|
|[編譯器警告（層級1） C4473](c4473.md)|'*function*'：傳遞給格式字串的引數不足|
|編譯器警告（層級3） C4474|'*function*'：傳遞給格式字串的引數太多|
|編譯器警告（層級3） C4475|'*function*'：長度修飾詞 '*修飾*詞 ' 不能與格式規範中的類型欄位字元 '*character*' 一起使用|
|編譯器警告（層級3） C4476|'*function*'：格式規範中的未知類型欄位字元 '*character*'|
|[編譯器警告（層級1） C4477](c4477.md)|'*function*'：格式字串 '*string*' 需要類型 '*type*' 的引數，但 variadic 引數*編號*具有類型 '*type*'|
|編譯器警告（層級1） C4478|'*function*'：不能在相同的格式字串中混合位置和非位置的預留位置|
|編譯器警告（錯誤） C4480|使用非標準的擴充：指定列舉 '*enumeration*' 的基礎類型|
|[編譯器警告（層級4） C4481](../../error-messages/compiler-warnings/compiler-warning-level-4-c4481.md)|使用非標準的擴充：覆寫規範 '*關鍵字*'|
|編譯器警告 C4482|使用非標準的擴充：在限定名稱中使用的列舉 '*enumeration*'|
|編譯器警告（層級1，錯誤） C4483|語法錯誤：預期C++的關鍵字|
|[編譯器警告（錯誤） C4484](../../error-messages/compiler-warnings/compiler-warning-c4484.md)|'*override_function*'：符合基底 ref 類別方法 '*base_class_function*'，但未標記為 ' virtual '、' new ' 或 ' override ';假設為 ' new ' （而非 ' virtual '）|
|[編譯器警告（錯誤） C4485](../../error-messages/compiler-warnings/compiler-warning-c4485.md)|'*override_function*'：符合基底 ref 類別方法 '*base_class_function*'，但未標記為 ' new ' 或 ' override ';假設為 ' new ' （和 ' virtual '）|
|[編譯器警告（層級1） C4486](../../error-messages/compiler-warnings/compiler-warning-level-1-c4486.md)|'*function*'： ref 類別或實值類別的私用虛擬方法應該標記為 ' sealed '|
|[編譯器警告（層級4） C4487](../../error-messages/compiler-warnings/compiler-warning-level-4-c4487.md)|'*derived_class_function*'：符合繼承的非虛擬方法 '*base_class_function*'，但未明確標記為 ' new '|
|[編譯器警告（層級1） C4488](../../error-messages/compiler-warnings/compiler-warning-level-1-c4488.md)|'*function*'：需要 '*關鍵字*' 關鍵字來執行介面方法 '*interface_method*'|
|[編譯器警告（層級1） C4489](../../error-messages/compiler-warnings/compiler-warning-level-1-c4489.md)|'*規範*'：不允許用在介面方法 '*method*';覆寫規範只允許用於 ref 類別和實值類別方法|
|[編譯器警告（層級1） C4490](../../error-messages/compiler-warnings/compiler-warning-level-1-c4490.md)|' override '：覆寫規範的使用不正確;'*function*' 與基底 ref 類別方法不符|
|編譯器警告（層級1） C4491|'*name*'：具有不合法的 IDL 版本格式|
|編譯器警告（層級1，錯誤） C4492|'*function1*'：符合基底 ref 類別方法 '*function2*'，但未標記為 ' override '|
|編譯器警告（層級3，錯誤） C4493|delete 運算式沒有作用，因為 '*type*' 的析構函式沒有 ' public ' 存取範圍|
|編譯器警告（層級1） C4494|'*function*'：忽略 __declspec （配置器），因為函式傳回型別不是指標或參考|
|編譯器警告 C4495|使用非標準的延伸模組 ' __super '：取代為明確的基類名稱|
|編譯器警告 C4496|針對每個使用非標準的延伸模組 '：取代為範圍-for 語句|
|編譯器警告 C4497|使用非標準的延伸模組 ' sealed '：取代為 ' final '|
|編譯器警告 C4498|使用非標準的擴充： '*extension*'|
|編譯器警告（層級4） C4499|'*function*'：明確特製化不能有儲存類別（已忽略）」|
|[編譯器警告（層級1） C4502](../../error-messages/compiler-warnings/compiler-warning-level-1-c4502.md)|'*連結規格*' 需要使用關鍵字 ' extern '，且必須在所有其他規範之前|
|[編譯器警告（層級1） C4503](../../error-messages/compiler-warnings/compiler-warning-level-1-c4503.md)|'*identifier*'：已超過裝飾名稱長度，名稱已被截斷|
|[編譯器警告（層級4） C4505](../../error-messages/compiler-warnings/compiler-warning-level-4-c4505.md)|'*function*'：已移除未參考的區域函式|
|[編譯器警告（層級1） C4506](../../error-messages/compiler-warnings/compiler-warning-level-1-c4506.md)|沒有內嵌函數 '*function*' 的定義|
|[編譯器警告（層級1） C4508](../../error-messages/compiler-warnings/compiler-warning-level-1-c4508.md)|'*function*'：函數應該傳回值;假設為 ' void ' 傳回類型|
|編譯器警告 C4509|使用非標準的擴充： '*function*' 使用 SEH，'*object*' 具有析構函式|
|[編譯器警告（層級4） C4510](../../error-messages/compiler-warnings/compiler-warning-level-4-c4510.md)|'*class*'：預設的構造函式已隱含定義為刪除|
|[編譯器警告（層級3） C4511](../../error-messages/compiler-warnings/compiler-warning-level-3-c4511.md)|'*class*'：複製的構造函式已隱含定義為刪除|
|[編譯器警告（層級4） C4512](../../error-messages/compiler-warnings/compiler-warning-level-4-c4512.md)|'*class*'：指派運算子已隱含定義為已刪除|
|[編譯器警告（層級4） C4513](../../error-messages/compiler-warnings/compiler-warning-level-4-c4513.md)|'*class*'：已將析構函式隱含定義為已刪除|
|[編譯器警告（層級4） C4514](../../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md)|'*function*'：已移除未參考的內嵌函數|
|[編譯器警告（層級4） C4515](../../error-messages/compiler-warnings/compiler-warning-level-4-c4515.md)|'*namespace*'：命名空間會使用本身|
|[編譯器警告（層級4） C4516](../../error-messages/compiler-warnings/compiler-warning-level-4-c4516.md)|' class：： symbol '：存取聲明已被取代;使用宣告的成員可以提供更好的替代方案|
|[編譯器警告（層級4） C4517](../../error-messages/compiler-warnings/compiler-warning-level-4-c4517.md)|存取宣告已被取代;使用宣告的成員可以提供更好的替代方案|
|[編譯器警告（層級1） C4518](../../error-messages/compiler-warnings/compiler-warning-level-1-c4518.md)|'*規範*'：此處非預期的儲存類別或類型規範;忽略|
|編譯器警告（錯誤） C4519|預設範本引數只允許用於類別樣板|
|[編譯器警告（層級3） C4521](../../error-messages/compiler-warnings/compiler-warning-level-3-c4521.md)|'*class*'：指定了多個複製的構造函式|
|[編譯器警告（層級3） C4522](../../error-messages/compiler-warnings/compiler-warning-level-3-c4522.md)|'*class*'：指定了多個指派運算子|
|[編譯器警告（層級3） C4523](../../error-messages/compiler-warnings/compiler-warning-level-3-c4523.md)|'*class*'：指定了多個析構函數|
|[編譯器警告（層級1） C4526](../../error-messages/compiler-warnings/compiler-warning-level-1-c4526.md)|'*function*'：靜態成員函式無法覆寫虛擬函式 '*virtual function*' 覆寫已忽略，虛擬函式將會隱藏|
|[編譯器警告（層級1） C4530](../../error-messages/compiler-warnings/compiler-warning-level-1-c4530.md)|C++使用了例外狀況處理常式，但未啟用回溯語義。 指定/EHsc|
|編譯器警告（層級1） C4531|C++Windows CE 上無法使用例外狀況處理。 使用結構化例外狀況處理|
|[編譯器警告（層級1） C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|' continue '：跳出 ' __finally/finally ' 區塊在終止處理期間有未定義的行為|
|[編譯器警告（層級1） C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|'*goto label*' 已略過 '*variable*' 的初始化|
|[編譯器警告（層級3） C4534](../../error-messages/compiler-warnings/compiler-warning-level-3-c4534.md)|由於預設引數的緣故 *，' ' 函式 ' 將*不是 ' class/struct ' '*identifier*' 的預設函式|
|[編譯器警告（層級3） C4535](../../error-messages/compiler-warnings/compiler-warning-level-3-c4535.md)|呼叫 _set_se_translator （）需要/EHa|
|[編譯器警告（層級4） C4536](../../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md)|'*typename*'：類型名稱超出中繼資料 '*character_limit*' 個字元的限制|
|[編譯器警告（層級1） C4537](../../error-messages/compiler-warnings/compiler-warning-level-1-c4537.md)|'*object*'： '. ' 適用于非 UDT 類型|
|[編譯器警告（層級3） C4538](../../error-messages/compiler-warnings/compiler-warning-level-3-c4538.md)|'*type*'：不支援此類型的 const/volatile 限定詞|
|[編譯器警告（層級1） C4540](../../error-messages/compiler-warnings/compiler-warning-level-1-c4540.md)|用來轉換成無法存取或不明確基底的 dynamic_cast;執行時間測試將會失敗（'*type1*' 至 '*type2*'）|
|[編譯器警告（層級1） C4541](../../error-messages/compiler-warnings/compiler-warning-level-1-c4541.md)|在具有/GR-的多型類型 '*type*' 上使用 '*identifier*';可能導致無法預期的行為|
|編譯器警告（層級1） C4542|略過合併插入文字檔的產生，無法寫入檔案*類型*檔案： '*issue*'：*訊息*|
|[編譯器警告（層級3） C4543](../../error-messages/compiler-warnings/compiler-warning-level-3-c4543.md)|由屬性 ' no\_injected_text ' 隱藏的插入文字|
|[編譯器警告（層級1） C4544](../../error-messages/compiler-warnings/compiler-warning-level-1-c4544.md)|'*宣告 '：* 在這個樣板宣告上忽略預設範本引數|
|[編譯器警告（層級1） C4545](../../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md)|逗號之前的運算式判斷值為遺漏引數清單的函式|
|[編譯器警告（層級1） C4546](../../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md)|逗號之前的函式呼叫遺漏引數清單|
|[編譯器警告（層級1） C4547](../../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md)|'*operator*'：逗號之前的運算子不會有任何作用;具有副作用的預期運算子|
|[編譯器警告（層級1） C4548](../../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md)|逗號之前的運算式無效; 必須是具有副作用的運算式|
|[編譯器警告（層級1） C4549](../../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md)|'*operator*'：逗號之前的運算子不會有任何作用;您想要 '*operator*' 嗎？|
|[編譯器警告（層級1） C4550](../../error-messages/compiler-warnings/compiler-warning-level-1-c4550.md)|運算式評估為遺漏引數清單的函式|
|[編譯器警告（層級1） C4551](../../error-messages/compiler-warnings/compiler-warning-level-1-c4551.md)|函式呼叫遺漏引數清單|
|[編譯器警告（層級1） C4552](../../error-messages/compiler-warnings/compiler-warning-level-1-c4552.md)|'*operator*'：運算子沒有作用;具有副作用的預期運算子|
|[編譯器警告（層級1） C4553](../../error-messages/compiler-warnings/compiler-warning-level-1-c4553.md)|'*operator*'：運算子沒有作用;您是否想要 ' operator？|
|[編譯器警告（層級3） C4554](../../error-messages/compiler-warnings/compiler-warning-level-3-c4554.md)C4554|'*operator*'：檢查運算子優先順序找出可能的錯誤;使用括弧來澄清優先順序|
|[編譯器警告（層級1） C4555](../../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md)|運算式無效; 必須是具有副作用的運算式|
|[編譯器警告（層級1） C4556](../../error-messages/compiler-warnings/compiler-warning-level-1-c4556.md)|內建函式直接引數 '*value*' 的值超出範圍 '*lower_bound*  -  *upper_bound*'|
|[編譯器警告（層級3） C4557](../../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md)|' __assume ' 包含效果 '*effect*'|
|[編譯器警告（層級1） C4558](../../error-messages/compiler-warnings/compiler-warning-level-1-c4558.md)|運算元 '*value*' 的值超出範圍 '*lower_bound*  -  *upper_bound*'|
|[編譯器警告（層級4） C4559](../../error-messages/compiler-warnings/compiler-warning-level-4-c4559.md)|'*function*'：重複定義;函數會取得 __declspec （修飾詞）|
|[編譯器警告（層級1） C4561](../../error-messages/compiler-warnings/compiler-warning-level-1-c4561.md)|' __fastcall ' 與 '/clr ' 選項不相容：轉換成 ' __stdcall '|
|編譯器警告（層級4） C4562|'/clr ' 選項需要完整的原型函數：將 ' （） ' 轉換為 ' （void） '|
|[編譯器警告（層級4） C4564](../../error-messages/compiler-warnings/compiler-warning-level-4-c4564.md)|' class ' '*classname*' 的方法 '*method*' 定義了不支援的預設參數 '*parameter*'|
|[編譯器警告（層級4） C4565](../../error-messages/compiler-warnings/compiler-warning-level-4-c4565.md)|'*function*'：重複定義;符號先前以 __declspec （修飾詞）宣告|
|[編譯器警告（層級1） C4566](../../error-messages/compiler-warnings/compiler-warning-level-1-c4566.md)|以通用字元名稱 '*char*' 表示的字元，無法在目前的字碼頁中表示（*數位*）|
|編譯器警告（層級1） C4568|'*function*'：沒有任何成員符合明確覆寫的簽章|
|編譯器警告（層級3） C4569|'*function*'：沒有任何成員符合明確覆寫的簽章|
|[編譯器警告（層級3） C4570](../../error-messages/compiler-warnings/compiler-warning-level-3-c4570.md)|'*type*'：未明確宣告為抽象，但有抽象函數|
|[編譯器警告（層級4） C4571](../../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md)|資訊： catch （...）自 Visual C++ 7.1 後已變更的語法;已不再攔截結構化例外狀況（SEH）|
|[編譯器警告（層級1） C4572](../../error-messages/compiler-warnings/compiler-warning-level-1-c4572.md)|[ParamArray] 屬性在/clr 下已被取代，請使用 ' ... '只|
|編譯器警告（層級1） C4573|使用 '*lambda function*' 時，編譯器必須先捕獲 ' this '，但目前的預設捕捉模式不允許它|
|編譯器警告（層級4） C4574|'*Identifier*' 已定義為 ' 0 '：您是指使用 ' #if Identifier ' 嗎？|
|編譯器警告（層級1） C4575|' __vectorcall ' 與 '/clr ' 選項不相容：轉換成 ' __stdcall '|
|編譯器警告（層級1，錯誤） C4576|後面接著初始化運算式清單的括弧型別為非標準的明確型別轉換語法|
|[編譯器警告（層級1，關閉） C4577](../../error-messages/compiler-warnings/compiler-warning-level-1-c4577.md)|使用了 ' noexcept '，但未指定例外狀況處理模式;不保證例外狀況的終止。 指定/EHsc|
|編譯器警告（層級1，錯誤） C4578|' abs '：從 '*type1*' 轉換成 '*type2*'，資料可能遺失（您是指呼叫 '*function*' 還是 #include \<h >？）|
|[編譯器警告（層級3） C4580](../../error-messages/compiler-warnings/compiler-warning-level-3-c4580.md)|[attribute] 已被取代；請改為指定 System::Attribute 或 Platform::Metadata 作為基底類別|
|[編譯器警告（層級1） C4581](../../error-messages/compiler-warnings/compiler-warning-level-1-c4581.md)|已取代的行為： ' "*字串*" ' 已取代為 '*string*' 以處理屬性|
|編譯器警告（層級4） C4582|'*type*'：未隱含呼叫此函式|
|編譯器警告（層級4） C4583|'*type*'：未隱含呼叫析構函式|
|[編譯器警告（層級1） C4584](../../error-messages/compiler-warnings/compiler-warning-level-1-c4584.md)|'*class1*'：基類 '*class2*' 已經是 '*a.class3*' 的基類|
|編譯器警告（層級1，錯誤） C4585|'*class*'：WinRT ' public ref class ' 必須是密封的，或衍生自現有的未密封類別|
|編譯器警告（層級1，錯誤） C4586|'*type*'：無法在名為 ' Windows ' 的最上層命名空間中宣告公用類型|
|編譯器警告（層級1） C4587|'*anonymous_structure*'：行為變更：不再隱含呼叫此函式|
|編譯器警告（層級1） C4588|'*anonymous_structure*'：行為變更：不再隱含呼叫析構函式|
|編譯器警告（層級1） C4591|已超過 ' constexpr ' 的呼叫深度限制（/constexpr：\<*深度編號 >* ）|
|編譯器警告（層級3） C4592|'*function*'： ' constexpr ' 呼叫評估失敗;函式將會在執行時間呼叫|
|編譯器警告（層級1） C4593|'*function*'： ' constexpr ' 呼叫評估步驟限制已超過 '*limit*';使用/constexpr：步驟\<號碼 > 以增加限制|
|編譯器警告（層級3） C4594|'*type*'：如果擲回例外狀況，則不會隱含呼叫析構函式|
|編譯器警告（層級1） C4595|'*type*'：行為變更：如果擲回例外狀況，則不會再隱含呼叫析構函式|
|[編譯器警告（層級4） C4596](../../error-messages/compiler-warnings/c4596.md)|'*identifier*'：成員宣告中有不合法的限定名稱|
|編譯器警告（錯誤） C4597|未定義的行為： offsetof 套用至虛擬基底的成員|
|編譯器警告（層級1和層級3） C4598|' #include "*標頭*" '：先行編譯頭*檔中的標頭編號不*符合該位置的目前編譯|
|編譯器警告（層級3）至 c4599|'*旗*標*路徑*'：命令列引數編號*編號*與先行編譯標頭檔不相符|

## <a name="see-also"></a>另請參閱

[C/C++編譯器和組建工具錯誤和警告](../compiler-errors-1/c-cpp-build-errors.md) \
[編譯器警告 C4000-至 c5999](compiler-warnings-c4000-c5999.md)
