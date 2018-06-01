---
title: 編譯器警告 C4400 透過 C4599 |Microsoft 文件
ms.date: 05/30/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
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
- C4451
- C4452
- C4453
- C4454
- C4455
- C4456
- C4457
- C4458
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
- C4458
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
dev_langs:
- C++
ms.assetid: b07850a5-ae89-48ea-bf9a-f0e30939f9b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 71dbf1817c43c5511f8ee711abf3ff3566f314c9
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704681"
---
# <a name="compiler-warnings-c4400-through-c4599"></a>編譯器警告 C4400 透過 C4599

文件的本節文章說明編譯器所產生的警告訊息的子集。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>警告訊息

|警告|訊息|
|-------------|-------------|
|[編譯器警告 (層級 1) C4600](compiler-warning-level-1-c4600.md)|#pragma '*巨集名稱*': 必須是有效的非空白字串|
|[編譯器警告 (層級 4) C4400](../../error-messages/compiler-warnings/compiler-warning-level-4-c4400.md)|'*類型*': 不支援此類型的 const/volatile 限定詞|
|[編譯器警告 (層級 1) C4401](../../error-messages/compiler-warnings/compiler-warning-level-1-c4401.md)|'*位元欄位*': 成員是位元欄位|
|[編譯器警告 (層級 1) C4402](../../error-messages/compiler-warnings/compiler-warning-level-1-c4402.md)|必須使用 PTR 運算子|
|[編譯器警告 (層級 1) C4403](../../error-messages/compiler-warnings/compiler-warning-level-1-c4403.md)|不合法的 PTR 運算子|
|[編譯器警告 (層級 3) C4404](../../error-messages/compiler-warnings/compiler-warning-level-3-c4404.md)|期限的已忽略指示詞|
|[編譯器警告 (層級 1) C4405](../../error-messages/compiler-warnings/compiler-warning-level-1-c4405.md)|'*識別碼*': 識別項是保留的字|
|[編譯器警告 (層級 1) C4406](../../error-messages/compiler-warnings/compiler-warning-level-1-c4406.md)|已忽略指示詞上的運算元|
|[編譯器警告 (層級 1) C4407](../../error-messages/compiler-warnings/compiler-warning-level-1-c4407.md)|不同成員指標表示法之間的轉換，編譯器可能會產生不正確的程式碼|
|[編譯器警告 (層級 4) C4408](../../error-messages/compiler-warnings/compiler-warning-level-4-c4408.md)|匿名 'struct&#124;等位' 沒有宣告任何資料成員|
|[編譯器警告 (層級 1) C4409](../../error-messages/compiler-warnings/compiler-warning-level-1-c4409.md)|不合法指令的大小|
|[編譯器警告 (層級 1) C4410](../../error-messages/compiler-warnings/compiler-warning-level-1-c4410.md)|運算元的大小不合法|
|[編譯器警告 (層級 1) C4411](../../error-messages/compiler-warnings/compiler-warning-level-1-c4411.md)|'*識別碼*': 符號解析至替代登錄|
|[編譯器警告 (層級 2) C4412](../../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md)|'*函式*': 函式簽章含有類型'*類型*';C + + 物件是純程式碼之間傳遞的不安全與混合或原生。|
|編譯器警告 C4413|'classname::member': 參考成員已初始化成建構函式結束之後，就不存在的暫存|
|[編譯器警告 (層級 3) C4414](../../error-messages/compiler-warnings/compiler-warning-level-3-c4414.md)|'*函式*': 函式的 short 跳躍指令被轉換為 near|
|編譯器警告 （層級 1） C4415|重複的 __declspec (code_seg ('*名稱*'))|
|編譯器警告 （層級 1） C4416|__declspec(code_seg(...)) 包含空字串： 忽略|
|編譯器警告 （層級 1） C4417|明確樣板具現化不能有 __declspec(code_seg(...))： 忽略|
|編譯器警告 （層級 1） C4418|__declspec(code_seg(...)) 忽略列舉|
|編譯器警告 （層級 3） C4419|'*符號*'時沒有任何作用套用至私用 ref 類別'*類別*'。|
|[編譯器警告 (層級 1) C4420](../../error-messages/compiler-warnings/compiler-warning-level-1-c4420.md)|'*checked_operator*': 無法使用運算子，使用'*運算子*' 代替; 執行階段檢查可能無法執行|
|編譯器警告 （層級 3） C4421|'*參數*': 參考參數，可繼續函式是可能不安全|
|編譯器警告 （層級 3） C4423|'std:: bad_alloc': 攔截到類別 ('*類型*') 的一行*數目*|
|編譯器警告 （層級 3） C4424|攔截的 '*type1*'前面加上'*type2*' 列上*數目*; 無法預期的行為可能會造成擲回 'std:: bad_alloc'|
|編譯器警告 （層級 1） C4425|SAL 註釋不能套用至 '...'|
|編譯器警告 （層級 1） C4426|包含標頭，可能是因為 #pragma optimize （） 之後變更的最佳化旗標|
|編譯器警告 （層級 1） C4427|'*運算子*': 常數相除，未定義的行為溢位|
|[編譯器警告 (層級 4) C4429](../../error-messages/compiler-warnings/compiler-warning-level-4-c4429.md)|可能不完整或格式不正確通用字元名稱|
|[編譯器警告 （錯誤） C4430](../../error-messages/compiler-warnings/compiler-warning-c4430.md)|遺漏類型規範 - 假設為 int。 注意： C + + 不支援 default-int|
|[編譯器警告 (層級 4) C4431](../../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md)|遺漏類型規範 - 假設為 int。 注意: C 已不再支援 default-int|
|[編譯器警告 (層級 4) C4434](../../error-messages/compiler-warnings/compiler-warning-level-4-c4434.md)|靜態建構函式必須具有私用存取範圍;變更為私用存取|
|[編譯器警告 (層級 4) C4435](../../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md)|'*derived_class*': /vd2 底下的物件配置將因虛擬基底而變更'*base_class*'|
|[編譯器警告 (層級 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)|動態\_轉換從虛擬基底 '*base_class*'to'*derived_class*' 建構函式或解構函式失敗，但是部分建構的物件|
|[編譯器警告 (層級 4) C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)|動態\_轉換從虛擬基底 '*base_class*'to'*derived_class*' 某些內容中可能會失敗|
|編譯器警告 C4438|'*函式*': 無法在中安全地呼叫 /await: clrcompat 模式。 如果 '*函式*' 呼叫 CLR，可能會導致 CLR 標頭損毀|
|[編譯器警告 （錯誤） C4439](../../error-messages/compiler-warnings/compiler-warning-c4439.md)|'*函式*': 函式簽章中有 managed 類型的定義必須有 __clrcall 呼叫慣例|
|[編譯器警告 (層級 1) C4440](../../error-messages/compiler-warnings/compiler-warning-level-1-c4440.md)|呼叫慣例的重複定義從 '*calling_convention1*'to'*calling_convenction2*' 忽略|
|[編譯器警告 (層級 1) C4441](../../error-messages/compiler-warnings/compiler-warning-level-1-c4441.md)|呼叫慣例 '*calling_convention1*' 忽略;'*calling_convention2*' 代替|
|編譯器警告 （層級 1） C4442|__annotation 引數中的內嵌 null 結束字元。  值會被截斷。|
|編譯器警告 （層級 1） C4443|pragma 參數必須為 '0'、 '1' 或 '2'|
|編譯器警告 （層級 3） C4444|'*識別碼*': 這個內容中不會實作最上層 '__unaligned'|
|[編譯器警告 (層級 1) C4445](../../error-messages/compiler-warnings/compiler-warning-level-1-c4445.md)|'*函式*': 在' WinRT&#124;managed' 類型的虛擬方法不可為私用|
|編譯器警告 （層級 1） C4446|'*類型*': 無法將對應的成員'*name1*' 至此類型，因為型別名稱發生衝突。 方法已重新命名為 '*name2*'|
|編譯器警告 （層級 1） C4447|發現沒有執行緒模型的 'main' 簽章。 請考慮使用 ' int main (platform:: array\<platform:: string ^ > ^ args)'。|
|編譯器警告 C4448|'*類型*1' 沒有中繼資料中指定的預設介面。 挑選: '*type2*'，這可能會在執行階段失敗。|
|編譯器警告 C4449|'*類型*' 非密封的類型應標記為 '[WebHostHidden]'|
|編譯器警告 C4450|'*type1*'應該標記為 '[WebHostHidden]' 因為其衍生自'*type2*'|
|編譯器警告 （層級 4） C4451|'classname1::member': ref 類別 'classname2::member' 在這個內容內的使用方式可能會導致不正確的封送處理物件跨內容|
|編譯器警告 （層級 1） C4452|'*識別碼*': 公用類型不能在全域範圍。 它必須是輸出.winmd 檔案名稱的子節點的命名空間中。|
|編譯器警告 （層級 1） C4453|'*類型*': '[WebHostHidden]' 類型不應之已發行介面上的公用型別不是 '[WebHostHidden]'|
|編譯器警告 （層級 1） C4454|'*函式*' 多個輸入參數數目所多載 [defaultoverload] 指定。 挑選 '*宣告*' 為預設多載|
|編譯器警告 （層級 1） C4455|' 運算子*運算子*': 不會啟動底線的常值後置字元識別項保留|
|[編譯器警告 (層級 4) C4456](compiler-warning-level-4-c4456.md)|宣告的 '*識別碼*' 會隱藏先前的區域宣告|
|[編譯器警告 (層級 4) C4457](compiler-warning-level-4-c4457.md)|宣告的 '*識別碼*' 會隱藏函式參數|
|[編譯器警告 (層級 4) C4458](compiler-warning-level-4-c4458.md)|宣告的 '*識別碼*' 會隱藏類別成員|
|[編譯器警告 （層級 4） C4459](compiler-warning-level-4-c4459.md)|宣告的 '*識別碼*' 會隱藏全域宣告|
|[編譯器警告 (層級 4) C4460](../../error-messages/compiler-warnings/compiler-warning-level-4-c4460.md)|'WinRT&#124;managed' 運算子'*運算子*'，具有參考所傳遞參數。 'WinRT&#124;managed' 運算子'*運算子*'具有來自 c + + 運算子的不同語意'*cpp_operator*'，您是否想要傳值方式傳遞？|
|[編譯器警告 (層級 1) C4461](../../error-messages/compiler-warnings/compiler-warning-level-1-c4461.md)|'*classname*': 這個類別具有完成項' ！*完成項*'，但沒有解構函式 ' ~*dtor*'|
|[編譯器警告 （層級 1，錯誤） C4462](../../error-messages/compiler-warnings/compiler-warning-level-1-c4462.md)|'*類型*': 無法判斷類型的 GUID。 程式可能在執行階段失敗。|
|[編譯器警告 （層級 4） C4463](compiler-warning-level-4-c4463.md)|溢位。指派 '*值*'給只能保留值的位元欄位'*min_value*'to'*max_value*'|
|[編譯器警告 (層級 4) C4464](../../error-messages/compiler-warnings/c4464.md)|相對 include 路徑包含 '..'|
|[編譯器警告 (層級 1) C4470](../../error-messages/compiler-warnings/compiler-warning-level-1-c4470.md)|浮點控制 pragma 在 /clr 下會忽略|
|[編譯器警告 （層級 4） C4471](compiler-warning-level-4-c4471.md)|'*列舉*': 不限範圍列舉的向前宣告必須含有基礎類型 (假設為 int)|
|編譯器警告 （層級 1） C4472|'*識別碼*' 是原生列舉： 新增存取規範 (private/public) 以便宣告 ' WinRT&#124;managed' 列舉|
|[編譯器警告 （層級 1） C4473](c4473.md)|'*函式*': 沒有足夠的引數傳遞給格式字串|
|編譯器警告 （層級 3） C4474|'*函式*': 太多引數傳遞給格式字串|
|編譯器警告 （層級 3） C4475|'*函式*': 長度修飾詞'*修飾詞*'不能與型別欄位字元'*字元*' 格式規範中|
|編譯器警告 （層級 3） C4476|'*函式*': 未知的型別欄位字元'*字元*' 格式規範中|
|[編譯器警告 （層級 1） C4477](c4477.md)|'*函式*': 格式字串'*字串*'需要類型的引數'*類型*'，但 variadic 引數*數目*具有類型 '*類型*'|
|編譯器警告 （層級 1） C4478|'*函式*': 無法在相同的格式字串中混合位置和非位置的預留位置|
|編譯器警告 C4480 （錯誤）|使用非標準擴充： 指定列舉的基礎型別 '*列舉*'|
|[編譯器警告 (層級 4) C4481](../../error-messages/compiler-warnings/compiler-warning-level-4-c4481.md)|使用非標準擴充： 覆寫規範 '*關鍵字*'|
|編譯器警告 C4482|使用非標準擴充： 列舉 '*列舉*' 限定名稱中使用|
|編譯器警告 （層級 1，錯誤） C4483|語法錯誤： 必須是 c + + 關鍵字|
|[編譯器警告 （錯誤） C4484](../../error-messages/compiler-warnings/compiler-warning-c4484.md)|'*override_function*': 符合基底 ref 類別方法'*base_class_function*'，但未標記為 'virtual'、 ' new' override';'new' （而非 'virtual'） 會假設|
|[編譯器警告 （錯誤） C4485](../../error-messages/compiler-warnings/compiler-warning-c4485.md)|'*override_function*': 符合基底 ref 類別方法'*base_class_function*'，但不是 '標示為 new' override';'new' （和 'virtual'） 會假設|
|[編譯器警告 (層級 1) C4486](../../error-messages/compiler-warnings/compiler-warning-level-1-c4486.md)|'*函式*': ref 類別或實值類別的私用虛擬方法標記為 'sealed'|
|[編譯器警告 (層級 4) C4487](../../error-messages/compiler-warnings/compiler-warning-level-4-c4487.md)|'*derived_class_function*': 符合繼承非虛擬方法'*base_class_function*'，但未明確標記為 'new'|
|[編譯器警告 (層級 1) C4488](../../error-messages/compiler-warnings/compiler-warning-level-1-c4488.md)|'*函式*': 需要'*關鍵字*'關鍵字來實作介面方法'*interface_method*'|
|[編譯器警告 (層級 1) C4489](../../error-messages/compiler-warnings/compiler-warning-level-1-c4489.md)|'*規範*': 不允許在介面方法'*方法*'; 覆寫規範只允許在 ref 類別和實值類別方法|
|[編譯器警告 (層級 1) C4490](../../error-messages/compiler-warnings/compiler-warning-level-1-c4490.md)|'override': 覆寫規範; 的用法不正確'*函式*' 不符合基底 ref 類別方法|
|編譯器警告 （層級 1） C4491|'*名稱*': 不合法的 IDL 版本格式|
|編譯器警告 （層級 1，錯誤） C4492|'*function1*': 符合基底 ref 類別方法'*function2*'，但未標記為 'override'|
|編譯器警告 （層級 3，錯誤） C4493|刪除運算式沒有任何作用的解構函式為 '*類型*' 沒有 'public' 可及性|
|編譯器警告 （層級 1） C4494|'*函式*': 忽略 __declspec （allocator），因為函式傳回型別不是指標或參考|
|編譯器警告 C4495|使用非標準擴充 ' __super ': 取代為明確的基底類別名稱|
|編譯器警告 C4496|使用非標準擴充 'for each': 取代為 ranged-for 陳述式|
|編譯器警告 C4497|使用非標準擴充 'sealed': 取代為 'final'|
|編譯器警告 C4498|使用非標準擴充: '*延伸*'|
|編譯器警告 （層級 4） C4499|*函式*': 明確特製化不能有儲存類別 （忽略） 」|
|[編譯器警告 (層級 1) C4502](../../error-messages/compiler-warnings/compiler-warning-level-1-c4502.md)|'*連結規格*' 必須使用關鍵字 'extern'，必須在所有其他規範之前|
|[編譯器警告 (層級 1) C4503](../../error-messages/compiler-warnings/compiler-warning-level-1-c4503.md)|'*識別碼*': 裝飾名稱長度超出範圍，名稱已遭截斷|
|[編譯器警告 (層級 4) C4505](../../error-messages/compiler-warnings/compiler-warning-level-4-c4505.md)|'*函式*': 已移除未參考的區域函式|
|[編譯器警告 (層級 1) C4506](../../error-messages/compiler-warnings/compiler-warning-level-1-c4506.md)|沒有定義內嵌函式的 '*函式*'|
|[編譯器警告 (層級 1) C4508](../../error-messages/compiler-warnings/compiler-warning-level-1-c4508.md)|'*函式*': 函式應傳回值。'void' 傳回假設的類型|
|編譯器警告 C4509|使用非標準擴充: '*函式*' 使用 SEH 和 '*物件*' 具有解構函式|
|[編譯器警告 (層級 4) C4510](../../error-messages/compiler-warnings/compiler-warning-level-4-c4510.md)|'*類別*': 預設建構函式已隱含定義為刪除|
|[編譯器警告 (層級 3) C4511](../../error-messages/compiler-warnings/compiler-warning-level-3-c4511.md)|'*類別*': 複製建構函式已隱含定義為刪除|
|[編譯器警告 (層級 4) C4512](../../error-messages/compiler-warnings/compiler-warning-level-4-c4512.md)|'*類別*': 指派運算子已隱含定義為刪除|
|[編譯器警告 (層級 4) C4513](../../error-messages/compiler-warnings/compiler-warning-level-4-c4513.md)|'*類別*': 解構函式已隱含定義為刪除|
|[編譯器警告 (層級 4) C4514](../../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md)|'*函式*': 已移除未參考的內嵌函式|
|[編譯器警告 (層級 4) C4515](../../error-messages/compiler-warnings/compiler-warning-level-4-c4515.md)|'*命名空間*': 命名空間使用本身|
|[編譯器警告 (層級 4) C4516](../../error-messages/compiler-warnings/compiler-warning-level-4-c4516.md)|'class::symbol': 已被取代存取宣告;成員 using 宣告提供較佳替代方式|
|[編譯器警告 (層級 4) C4517](../../error-messages/compiler-warnings/compiler-warning-level-4-c4517.md)|不再支援存取宣告;成員 using 宣告提供較佳替代方式|
|[編譯器警告 (層級 1) C4518](../../error-messages/compiler-warnings/compiler-warning-level-1-c4518.md)|'*規範*': 非預期的儲存類別或類型規範; 忽略|
|編譯器警告 （錯誤） C4519|預設範本引數只允許出現在類別樣板|
|[編譯器警告 (層級 3) C4521](../../error-messages/compiler-warnings/compiler-warning-level-3-c4521.md)|'*類別*': 多個複製建構函式指定|
|[編譯器警告 (層級 3) C4522](../../error-messages/compiler-warnings/compiler-warning-level-3-c4522.md)|'*類別*': 多個指定的指派運算子|
|[編譯器警告 (層級 3) C4523](../../error-messages/compiler-warnings/compiler-warning-level-3-c4523.md)|'*類別*': 多個指定的解構函式|
|[編譯器警告 (層級 1) C4526](../../error-messages/compiler-warnings/compiler-warning-level-1-c4526.md)|'*函式*': 靜態成員函式不能覆寫虛擬函式'*虛擬函式*' 覆寫被忽略，將會隱藏虛擬函式|
|[編譯器警告 (層級 1) C4530](../../error-messages/compiler-warnings/compiler-warning-level-1-c4530.md)|C + + 例外狀況處理常式使用，但回溯語意不會啟用。 指定 /EHsc|
|編譯器警告 （層級 1） C4531|C + + 例外狀況處理 Windows CE 上無法使用。 使用結構化例外狀況處理|
|[編譯器警告 (層級 1) C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|'continue': 跳出 '__finally/finally' 區塊有未定義的行為在終止處理期間|
|[編譯器警告 (層級 1) C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|初始化 '*變數*'會被略過'*goto 標籤*'|
|[編譯器警告 (層級 3) C4534](../../error-messages/compiler-warnings/compiler-warning-level-3-c4534.md)|'*建構函式*'才能' 類別/結構 '的預設建構函式'*識別碼*' 由於預設引數|
|[編譯器警告 (層級 3) C4535](../../error-messages/compiler-warnings/compiler-warning-level-3-c4535.md)|呼叫 _set_se_translator() 需要 /EHa|
|[編譯器警告 (層級 4) C4536](../../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md)|'*typename*': 類型名稱超出中繼資料的限制'*character_limit*' 字元|
|[編譯器警告 (層級 1) C4537](../../error-messages/compiler-warnings/compiler-warning-level-1-c4537.md)|'*物件*': '。' 套用至非 UDT 類型|
|[編譯器警告 (層級 3) C4538](../../error-messages/compiler-warnings/compiler-warning-level-3-c4538.md)|'*類型*': 不支援此類型的 const/volatile 限定詞|
|[編譯器警告 (層級 1) C4540](../../error-messages/compiler-warnings/compiler-warning-level-1-c4540.md)|用來將轉換成無法存取或模稜兩可的基底; dynamic_cast執行階段測試將會失敗 ('*type1*'to'*type2*')|
|[編譯器警告 (層級 1) C4541](../../error-messages/compiler-warnings/compiler-warning-level-1-c4541.md)|'*識別碼*'用於多型型別'*類型*' 可能會造成無法預期的行為與 /GR-;|
|編譯器警告 （層級 1） C4542|正在略過合併插入的文字檔案產生無法寫入*filetype*檔案: '*問題*':*訊息*|
|[編譯器警告 (層級 3) C4543](../../error-messages/compiler-warnings/compiler-warning-level-3-c4543.md)|插入文字隱藏的屬性 ' 沒有\_injected_text'|
|[編譯器警告 (層級 1) C4544](../../error-messages/compiler-warnings/compiler-warning-level-1-c4544.md)|'*宣告*': 預設會忽略這個樣板宣告上的樣板引數|
|[編譯器警告 (層級 1) C4545](../../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md)|逗號之前的運算式判斷值為遺漏引數清單的函式|
|[編譯器警告 (層級 1) C4546](../../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md)|逗號之前的函式呼叫遺漏引數清單|
|[編譯器警告 (層級 1) C4547](../../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md)|'*運算子*': 運算子逗號之前無效; 必須是具有副作用的運算子|
|[編譯器警告 (層級 1) C4548](../../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md)|逗號之前的運算式無效; 必須是具有副作用的運算式|
|[編譯器警告 (層級 1) C4549](../../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md)|'*運算子*': 逗號之前的運算子無效; 您是否想'*運算子*' 嗎？|
|[編譯器警告 (層級 1) C4550](../../error-messages/compiler-warnings/compiler-warning-level-1-c4550.md)|運算式評估為遺漏引數清單的函式|
|[編譯器警告 (層級 1) C4551](../../error-messages/compiler-warnings/compiler-warning-level-1-c4551.md)|函式呼叫遺漏引數清單|
|[編譯器警告 (層級 1) C4552](../../error-messages/compiler-warnings/compiler-warning-level-1-c4552.md)|'*運算子*': 運算子無效; 必須是具有副作用的運算子|
|[編譯器警告 (層級 1) C4553](../../error-messages/compiler-warnings/compiler-warning-level-1-c4553.md)|'*運算子*': 運算子無效; 您是否想' 運算子嗎？|
|[編譯器警告 （層級 3） C4554](../../error-messages/compiler-warnings/compiler-warning-level-3-c4554.md) C4554|'*運算子*': 檢查運算子優先順序找出可能發生錯誤; 使用括號釐清順序|
|[編譯器警告 (層級 1) C4555](../../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md)|運算式無效; 必須是具有副作用的運算式|
|[編譯器警告 (層級 1) C4556](../../error-messages/compiler-warnings/compiler-warning-level-1-c4556.md)|內建函式直接引數的值 '*值*'超出範圍'*lower_bound* - *upper_bound*'|
|[編譯器警告 (層級 3) C4557](../../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md)|'__assume' 包含作用 '*效果*'|
|[編譯器警告 (層級 1) C4558](../../error-messages/compiler-warnings/compiler-warning-level-1-c4558.md)|運算元的值 '*值*'超出範圍'*lower_bound* - *upper_bound*'|
|[編譯器警告 (層級 4) C4559](../../error-messages/compiler-warnings/compiler-warning-level-4-c4559.md)|'*函式*': 重複定義; 函式提升 __declspec(modifier)|
|[編譯器警告 (層級 1) C4561](../../error-messages/compiler-warnings/compiler-warning-level-1-c4561.md)|'__fastcall' 不以 '/ /clr' 選項： 將轉換為 '__stdcall'|
|編譯器警告 （層級 4） C4562|完全原型函式是必要項目 '/ /clr' 選項： 轉換為 '(void)' 的 ' （）'|
|[編譯器警告 (層級 4) C4564](../../error-messages/compiler-warnings/compiler-warning-level-4-c4564.md)|方法 '*方法*'的 'class''*classname*'定義不支援的預設參數'*參數*'|
|[編譯器警告 (層級 4) C4565](../../error-messages/compiler-warnings/compiler-warning-level-4-c4565.md)|'*函式*': 重複定義; 符號先前已宣告為 __declspec(modifier)|
|[編譯器警告 (層級 1) C4566](../../error-messages/compiler-warnings/compiler-warning-level-1-c4566.md)|通用字元名稱所代表的字元 '*char*' 無法在目前的字碼頁中 (*數目*)|
|編譯器警告 （層級 1） C4568|'*函式*': 沒有任何成員符合明確覆寫的簽章|
|編譯器警告 （層級 3） C4569|'*函式*': 沒有任何成員符合明確覆寫的簽章|
|[編譯器警告 (層級 3) C4570](../../error-messages/compiler-warnings/compiler-warning-level-3-c4570.md)|'*類型*': 未明確宣告為抽象，但是擁有抽象函式|
|[編譯器警告 (層級 4) C4571](../../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md)|Visual c + + 7.1; 以來變更的告知性： catch 語意不再攔截結構化例外狀況 (SEH)|
|[編譯器警告 (層級 1) C4572](../../error-messages/compiler-warnings/compiler-warning-level-1-c4572.md)|/Clr 底下的 [ParamArray] 屬性已被取代，請使用 '...' 改為|
|編譯器警告 （層級 1） C4573|使用 '*lambda 函式*' 需要編譯器擷取 'this'，但目前的預設擷取模式不允許使用它|
|編譯器警告 （層級 4） C4574|'*識別碼*'定義為' 0': 您是否想要使用 '#if identifier'？|
|編譯器警告 （層級 1） C4575|'__vectorcall' 不以 '/ /clr' 選項： 將轉換為 '__stdcall'|
|編譯器警告 （層級 1，錯誤） C4576|後面接著以初始設定式清單是括號括住類型為非標準的明確類型轉換語法|
|編譯器警告 （層級 1，設為 Off） C4577|任何例外狀況處理模式指定; 使用 ' noexcept'不保證終止的例外狀況。 指定 /EHsc|
|編譯器警告 （層級 1，錯誤） C4578|'abs': 從轉換 '*type1*'to'*type2*'，可能導致資料遺失 (您是否想要呼叫'*函式*' 或 #include \<h >？)|
|[編譯器警告 (層級 3) C4580](../../error-messages/compiler-warnings/compiler-warning-level-3-c4580.md)|[attribute] 已被取代；請改為指定 System::Attribute 或 Platform::Metadata 作為基底類別|
|[編譯器警告 (層級 1) C4581](../../error-messages/compiler-warnings/compiler-warning-level-1-c4581.md)|已被取代的行為: '"*字串*"' 取代 '*字串*' 處理序屬性|
|編譯器警告 （層級 4） C4582|'*類型*': 未隱含呼叫建構函式|
|編譯器警告 （層級 4） C4583|'*類型*': 未隱含呼叫解構函式|
|[編譯器警告 (層級 1) C4584](../../error-messages/compiler-warnings/compiler-warning-level-1-c4584.md)|'*class1*': 基底類別'*class2*'已經的基底類別'*class3 移*'|
|編譯器警告 （層級 1，錯誤） C4585|'*類別*': WinRT 'public ref class' 必須密封或衍生自現有的未密封類別|
|編譯器警告 （層級 1，錯誤） C4586|'*類型*': 無法在名稱為 'Windows' 的最上層命名空間宣告的公用型別|
|編譯器警告 （層級 1） C4587|'*anonymous_structure*': 行為變更： 不再隱含呼叫建構函式|
|編譯器警告 （層級 1） C4588|'*anonymous_structure*': 行為變更： 不再隱含呼叫解構函式|
|編譯器警告 （層級 1） C4591|'constexpr' 呼叫深度限制*數目*超過 (/: depth<n>\<數字 >)|
|編譯器警告 （層級 3） C4592|'*函式*': 'constexpr' 呼叫評估失敗，則會在執行階段呼叫函式|
|編譯器警告 （層級 1） C4593|'*函式*': 'constexpr' 呼叫評估步驟限制'*限制*' 超過; 使用 /constexpr:\<數字 > 以提高的限制|
|編譯器警告 （層級 3） C4594|'*類型*': 解構函式將不會隱含地呼叫發生例外狀況|
|編譯器警告 （層級 1） C4595|'*類型*': 行為變更： 呼叫解構函式將不再會隱含地發生例外狀況|
|編譯器警告 （層級 4） C4596|'*識別碼*': 成員宣告中不合法的限定的名稱|
|編譯器警告 （錯誤） C4597|未定義的行為： offsetof 套用至虛擬基底成員|
|編譯器警告 （層級 1 和層級 3） C4598|' #include"*標頭*"': 標頭數目*數目*先行編譯標頭中不符合目前在該位置的編譯|
|編譯器警告 （層級 3） C4599|'*旗標**路徑*': 命令列引數數目*數目*不符先行編譯標頭|
