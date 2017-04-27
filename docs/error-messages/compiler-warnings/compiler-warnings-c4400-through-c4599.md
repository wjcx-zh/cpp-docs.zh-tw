---
title: "編譯器警告 C4400 透過 C4599 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- C4463
- C4464
- C4471
- C4472
- C4480
- C4482
- C4483
- C4491
- C4492
- C4493
- C4494
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
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 4bac7b2942f9d72674b8092dc7bf64174dd3c349
ms.openlocfilehash: 59f50ea77dee36b982bf5d78e86a2a6a4d37ec54
ms.lasthandoff: 04/24/2017

---
# <a name="compiler-warnings-c4400-through-c4599"></a>編譯器警告 C4400 透過 C4599
這一部分的文件中的文章包含 Visual c + + 編譯器警告的資訊子集。 您可以在此存取資訊或在**輸出**視窗在 Visual Studio 中，您可以選取警告代碼，然後選擇 F1 鍵。  
  
> [!NOTE]
>  並非每個[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]錯誤或警告會記載於 MSDN 中。 在許多情況下，診斷訊息會提供所有可用的資訊。 如果您認為錯誤訊息需要補充說明，請告訴我們。 您可以使用這個頁面上的回函表單或移至 Visual Studio 中的功能表列並選擇**協助**，**回報 Bug**，或您可以提出建議或 bug 報告上[Microsoft Connect](http://connect.microsoft.com/VisualStudio)。  
  
您可能會發現其他協助的 MSDN 公共論壇上錯誤及警告。 [Visual c + + 語言](http://go.microsoft.com/fwlink/?LinkId=158195)論壇是關於問題及討論[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]語言語法和編譯器。 [Visual c + + 一般](http://go.microsoft.com/fwlink/?LinkId=158194)論壇是關於問題[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]其他論壇中沒有討論之。 您也可能會在找到關於錯誤和警告的說明[堆疊溢位](http://stackoverflow.com/)。  
  
## <a name="in-this-section"></a>本章節內容  
  
|警告|訊息|  
|-------------|-------------|  
|[編譯器警告 (層級 1) C4600](../../error-messages/compiler-warnings/compiler-warning-level-1-c4600.md)|#pragma '巨集名稱': 必須是有效的非空白字串|  
|[編譯器警告 (層級 4) C4400](../../error-messages/compiler-warnings/compiler-warning-level-4-c4400.md)|'type': 不支援此類型的 const/volatile 限定詞|  
|[編譯器警告 (層級 1) C4401](../../error-messages/compiler-warnings/compiler-warning-level-1-c4401.md)|'位元欄位': 成員是位元欄位|  
|[編譯器警告 (層級 1) C4402](../../error-messages/compiler-warnings/compiler-warning-level-1-c4402.md)|必須使用 PTR 運算子|  
|[編譯器警告 (層級 1) C4403](../../error-messages/compiler-warnings/compiler-warning-level-1-c4403.md)|不合法的 PTR 運算子|  
|[編譯器警告 (層級 3) C4404](../../error-messages/compiler-warnings/compiler-warning-level-3-c4404.md)|已忽略指示詞前的句號|  
|[編譯器警告 (層級 1) C4405](../../error-messages/compiler-warnings/compiler-warning-level-1-c4405.md)|'identifier': 識別項是保留的字|  
|[編譯器警告 (層級 1) C4406](../../error-messages/compiler-warnings/compiler-warning-level-1-c4406.md)|已忽略指示詞上的運算元|  
|[編譯器警告 (層級 1) C4407](../../error-messages/compiler-warnings/compiler-warning-level-1-c4407.md)|在不同的成員指標表示法間進行轉換，可能導致編譯器產生不正確的程式碼|  
|[編譯器警告 (層級 4) C4408](../../error-messages/compiler-warnings/compiler-warning-level-4-c4408.md)|匿名 'struct &#124; 等位' 沒有宣告任何資料成員|  
|[編譯器警告 (層級 1) C4409](../../error-messages/compiler-warnings/compiler-warning-level-1-c4409.md)|指令的大小不合法|  
|[編譯器警告 (層級 1) C4410](../../error-messages/compiler-warnings/compiler-warning-level-1-c4410.md)|運算元的大小不合法|  
|[編譯器警告 (層級 1) C4411](../../error-messages/compiler-warnings/compiler-warning-level-1-c4411.md)|'identifier': 符號解析至替代登錄|  
|[編譯器警告 (層級 2) C4412](../../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md)|'function': 函式簽章含有類型 'type';C + + 物件是純程式碼之間傳遞的不安全與混合或原生。|  
|編譯器警告 C4413|'classname::member': 參考成員已初始化成建構函式結束之後，就不存在的暫存|  
|[編譯器警告 (層級 3) C4414](../../error-messages/compiler-warnings/compiler-warning-level-3-c4414.md)|'function': 函式的 short 跳躍指令被轉換為 near|  
|編譯器警告 （層級 1） C4415|複製 __declspec(code_seg('%$I'))|  
|編譯器警告 （層級 1） C4416|__declspec(code_seg(...)) 包含空字串: 已忽略|  
|編譯器警告 （層級 1） C4417|明確樣板具現化不能有 __declspec(code_seg(...)): 已忽略|  
|編譯器警告 （層級 1） C4418|__declspec(code_seg(...)) 在型舉上已忽略|  
|編譯器警告 （層級 3） C4419|'%$I' 在套用至私用 ref 類別 '%$S' 時無效。|  
|[編譯器警告 (層級 1) C4420](../../error-messages/compiler-warnings/compiler-warning-level-1-c4420.md)|'checked_operator': 無法使用運算子，改用 'operator';執行階段檢查可能無法執行|  
|編譯器警告 （層級 3） C4421|'%$I': 可繼續函式的參考參數可能不安全|  
|編譯器警告 （層級 3） C4423|'std::bad_alloc': 將由類別 ('%$T') 攔截 (第 %d 行)|  
|編譯器警告 （層級 3） C4424|'%$T' 的攔截之前是 '%$T' (第 %d 行); 如果擲回 'std::bad_alloc'，可能發生無法預期的行為|  
|編譯器警告 （層級 1） C4425|無法將 SAL 註釋套用至 '...'|  
|編譯器警告 C4426|包含標頭，可能是因為 #pragma optimize （） 之後變更的最佳化旗標|  
|編譯器警告 （層級 1） C4427|'%$L': 常數相除溢位，此為未定義的行為|  
|[編譯器警告 (層級 4) C4429](../../error-messages/compiler-warnings/compiler-warning-level-4-c4429.md)|可能是不完整或格式不當的通用字元名稱|  
|[編譯器警告 C4430](../../error-messages/compiler-warnings/compiler-warning-c4430.md)|遺漏類型規範 - 假設為 int。 注意︰ C + + 不支援 default-int|  
|[編譯器警告 (層級 4) C4431](../../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md)|遺漏類型規範 - 假設為 int。 注意: C 已不再支援 default-int|  
|[編譯器警告 (層級 4) C4434](../../error-messages/compiler-warnings/compiler-warning-level-4-c4434.md)|靜態建構函式必須有私用存取範圍; 已變更為私用存取|  
|[編譯器警告 (層級 4) C4435](../../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md)|'derived_class': /vd2 底下的物件配置將因虛擬基底 'base_class' 而變更|  
|[編譯器警告 (層級 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)|從虛擬基底 'base_class' dynamic_cast 'derived_class' 建構函式或解構函式失敗，但是部分建構的物件|  
|[編譯器警告 (層級 4) C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)|在某些內容中無法從虛擬基底 'base_class' 到 'derived_class' 的 dynamic_cast|  
|編譯器警告 C4438|'%$S': 無法在中安全地呼叫 /await: clrcompat 模式。 如果 '%$S' 呼叫 CLR，可能導致 CLR 標頭損毀|  
|[編譯器警告 C4439](../../error-messages/compiler-warnings/compiler-warning-c4439.md)|'function': 函式簽章中有 managed 類型的定義必須有 __clrcall 呼叫慣例|  
|[編譯器警告 (層級 1) C4440](../../error-messages/compiler-warnings/compiler-warning-level-1-c4440.md)|呼叫慣例 'calling_convenction2' 略過從 'calling_convention1' 重複定義|  
|[編譯器警告 (層級 1) C4441](../../error-messages/compiler-warnings/compiler-warning-level-1-c4441.md)|呼叫慣例 'calling_convention1' 忽略;' calling_convention2' 代替|  
|編譯器警告 （層級 1） C4442|__annotation 引數中的內嵌 null 結束字元。  值會被截斷。|  
|編譯器警告 （層級 1） C4443|pragma 參數必須是 '0'、'1' 或 '2'|  
|編譯器警告 （層級 3） C4444|'identifier': 這個內容中不會實作最上層 '__unaligned'|  
|[編譯器警告 (層級 1) C4445](../../error-messages/compiler-warnings/compiler-warning-level-1-c4445.md)|'function': 在 ' WinRT &#124; managed' 類型的虛擬方法不可為私用|  
|編譯器警告 （層級 1） C4446|'%$S': 無法將對應的成員 '%$I' 至此類型，因為衝突的類型名稱。 方法已重新命名為 ' %$I '|  
|編譯器警告 （層級 1） C4447|發現沒有執行緒模型的 'main' 簽章。 請考慮使用 ' int main (platform:: array\<platform:: string ^ > ^ args)'。|  
|編譯器警告 C4448|'%$S' 並沒有中繼資料中指定的預設介面。 挑選: '%$S'，這可能會在執行階段失敗。|  
|編譯器警告 C4449|'%$S' 非密封的類型應標記為 '[WebHostHidden]'|  
|編譯器警告 C4450|'%$S' 應該標記為 '[WebHostHidden]'，因為其衍生自 '%$S'|  
|編譯器警告 （層級 4） C4451|'classname1::member': ref 類別 'classname2::member' 在這個內容內的使用方式可能會導致不正確的封送處理物件跨內容|  
|編譯器警告 （層級 1） C4452|'identifier': 公用類型不能在全域範圍。 它必須是輸出.winmd 檔案名稱的子節點的命名空間中。|  
|編譯器警告 （層級 1） C4453|'%$S': '[WebHostHidden]' 類型不應之已發行介面上的公用型別不是 '[WebHostHidden]'|  
|編譯器警告 （層級 1） C4454|'%$S' 為多個輸入參數數目多載，而不需要指定 [DefaultOverload]。 挑選為預設多載的 '%$D'|  
|編譯器警告 （層級 1） C4455|'operator %$I': 開頭不是底線的常值後置字元識別項已予保留|  
|編譯器警告 （層級 3） C4456|'identifier' 的宣告會隱藏先前的區域宣告|  
|編譯器警告 （層級 3） C4457|'identifier' 的宣告會隱藏函式參數|  
|編譯器警告 （層級 3） C4458|'identifier' 的宣告會隱藏類別成員|  
|編譯器警告 （層級 3） C4459|'identifier' 的宣告會隱藏全域宣告|  
|[編譯器警告 (層級 4) C4460](../../error-messages/compiler-warnings/compiler-warning-level-4-c4460.md)|' WinRT &#124; managed' 運算子 'operator'，有傳址方式傳遞的參數。 ' WinRT &#124; managed' 運算子 'operator' 具有來自 c + + 運算子的不同語意 'cpp_operator'，您要以傳值方式傳遞？|  
|[編譯器警告 (層級 1) C4461](../../error-messages/compiler-warnings/compiler-warning-level-1-c4461.md)|'classname': 這個類別具有完成項 '！ finalizer'，但沒有解構函式' ~ dtor'|  
|[編譯器警告 (層級 1) C4462](../../error-messages/compiler-warnings/compiler-warning-level-1-c4462.md)|'type': 無法判斷類型的 GUID。 程式可能在執行階段失敗。|  
|編譯器警告 C4463|溢位。將 'value' 指派給只能保留值 'mi_valuen' 到 'max_value' 的位元欄位|  
|編譯器警告 C4464|相對 include 路徑包含 '..'|  
|[編譯器警告 (層級 1) C4470](../../error-messages/compiler-warnings/compiler-warning-level-1-c4470.md)|浮點控制 pragma 在 /clr 下會被忽略|  
|編譯器警告 （層級 4） C4471|'enumeration': 不限範圍列舉的向前宣告必須含有基礎類型 (假設為 int)|  
|編譯器警告 （層級 1） C4472|'identifier' 是原生列舉︰ 新增存取規範 (private/public) 以便宣告 ' WinRT &#124; managed' 列舉|  
|編譯器警告 C4480|使用非標準擴充︰ 指定列舉 'enumeration' 的基礎類型|  
|[編譯器警告 (層級 4) C4481](../../error-messages/compiler-warnings/compiler-warning-level-4-c4481.md)|使用非標準擴充︰ 覆寫規範 'keyword'|  
|編譯器警告 C4482|使用非標準擴充︰ 列舉 'enumeration' 限定名稱中使用|  
|編譯器警告 （層級 1） C4483|語法錯誤: 必須是 C++ 關鍵字|  
|[編譯器警告 C4484](../../error-messages/compiler-warnings/compiler-warning-c4484.md)|'override_function': 符合基底 ref 類別方法 'base_class_function'，但未標記為 'virtual'、 ' new' override';'new' （而非 'virtual'） 會假設|  
|[編譯器警告 C4485](../../error-messages/compiler-warnings/compiler-warning-c4485.md)|'override_function': 符合基底 ref 類別方法 'base_class_function'，但不是標示為 'new' override';'new' （和 'virtual'） 會假設|  
|[編譯器警告 (層級 1) C4486](../../error-messages/compiler-warnings/compiler-warning-level-1-c4486.md)|'function': ref 類別或實值類別的私用虛擬方法標記為 'sealed'|  
|[編譯器警告 (層級 4) C4487](../../error-messages/compiler-warnings/compiler-warning-level-4-c4487.md)|'derived_class_function': 符合繼承的非虛擬方法 'base_class_function'，但未明確標記為 'new'|  
|[編譯器警告 (層級 1) C4488](../../error-messages/compiler-warnings/compiler-warning-level-1-c4488.md)|'function': 需要 'keyword' 關鍵字來實作介面方法 'interface_method'|  
|[編譯器警告 (層級 1) C4489](../../error-messages/compiler-warnings/compiler-warning-level-1-c4489.md)|'specifier': 不允許在介面方法 'method';覆寫規範只允許在 ref 類別和實值類別方法|  
|[編譯器警告 (層級 1) C4490](../../error-messages/compiler-warnings/compiler-warning-level-1-c4490.md)|'override': 覆寫規範; 的用法不正確'function' 不符合基底 ref 類別方法|  
|編譯器警告 （層級 1） C4491|'%s': 有不合法的 IDL 版本格式|  
|編譯器警告 （層級 1） C4492|'%$S': 符合基底 ref 類別方法 '%$S'，但是未標記為 'override'|  
|編譯器警告 （層級 3） C4493|刪除運算式任何作用，因為沒有 'public' 可及性的解構函式的 'type'。|  
|編譯器警告 （層級 1） C4494|'%$S' : 忽略 __declspec(allocator)，因為函式傳回的類型不是指標或參考|  
|[編譯器警告 (層級 1) C4502](../../error-messages/compiler-warnings/compiler-warning-level-1-c4502.md)|'連結規格' 必須使用關鍵字 'extern' 且必須在其他規範之前|  
|[編譯器警告 (層級 1) C4503](../../error-messages/compiler-warnings/compiler-warning-level-1-c4503.md)|'identifier': 裝飾名稱長度超出範圍，名稱已遭截斷|  
|[編譯器警告 (層級 4) C4505](../../error-messages/compiler-warnings/compiler-warning-level-4-c4505.md)|'function': 已移除未參考的區域函式|  
|[編譯器警告 (層級 1) C4506](../../error-messages/compiler-warnings/compiler-warning-level-1-c4506.md)|沒有內嵌函式 'function' 的定義|  
|[編譯器警告 (層級 1) C4508](../../error-messages/compiler-warnings/compiler-warning-level-1-c4508.md)|'function': 函式應傳回值。'void' 傳回假設的類型|  
|編譯器警告 C4509|使用非標準擴充: 'function' 使用 SEH 且 'object' 具有解構函式|  
|[編譯器警告 (層級 4) C4510](../../error-messages/compiler-warnings/compiler-warning-level-4-c4510.md)|'class': 預設建構函式已隱含定義為刪除|  
|[編譯器警告 (層級 3) C4511](../../error-messages/compiler-warnings/compiler-warning-level-3-c4511.md)|'class': 複製建構函式已隱含定義為刪除|  
|[編譯器警告 (層級 4) C4512](../../error-messages/compiler-warnings/compiler-warning-level-4-c4512.md)|'class': 指派運算子已隱含定義為刪除|  
|[編譯器警告 (層級 4) C4513](../../error-messages/compiler-warnings/compiler-warning-level-4-c4513.md)|'class': 解構函式已隱含定義為刪除|  
|[編譯器警告 (層級 4) C4514](../../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md)|'function': 已移除未參考的內嵌函式|  
|[編譯器警告 (層級 4) C4515](../../error-messages/compiler-warnings/compiler-warning-level-4-c4515.md)|'namespace': 命名空間使用本身|  
|[編譯器警告 (層級 4) C4516](../../error-messages/compiler-warnings/compiler-warning-level-4-c4516.md)|'class::symbol': 已被取代存取宣告;成員 using 宣告提供較佳替代方式|  
|[編譯器警告 (層級 4) C4517](../../error-messages/compiler-warnings/compiler-warning-level-4-c4517.md)|不鼓勵使用存取宣告; 建議使用成員 using 宣告代替|  
|[編譯器警告 (層級 1) C4518](../../error-messages/compiler-warnings/compiler-warning-level-1-c4518.md)|'specifier': 儲存類別或這裡; 型別未預期的規範忽略|  
|編譯器警告 C4519|預設的樣板引數只能用於類別樣板|  
|[編譯器警告 (層級 3) C4521](../../error-messages/compiler-warnings/compiler-warning-level-3-c4521.md)|'class': 多個複製建構函式指定|  
|[編譯器警告 (層級 3) C4522](../../error-messages/compiler-warnings/compiler-warning-level-3-c4522.md)|'class': 多個指定的指派運算子|  
|[編譯器警告 (層級 3) C4523](../../error-messages/compiler-warnings/compiler-warning-level-3-c4523.md)|'class': 多個指定的解構函式|  
|[編譯器警告 (層級 1) C4526](../../error-messages/compiler-warnings/compiler-warning-level-1-c4526.md)|'function': 靜態成員函式不能覆寫虛擬函式 '虛擬函式' \n 覆寫被忽略，將會隱藏虛擬函式|  
|[編譯器警告 (層級 1) C4530](../../error-messages/compiler-warnings/compiler-warning-level-1-c4530.md)|C + + 例外狀況處理常式使用，但回溯語意不會啟用。 指定 /EHsc|  
|編譯器警告 （層級 1） C4531|C + + 例外狀況處理 Windows CE 上無法使用。 使用結構化例外狀況處理|  
|[編譯器警告 (層級 1) C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|'continue': 跳出 '__finally/finally' 區塊有未定義的行為在終止處理期間|  
|[編譯器警告 (層級 1) C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|'variable' 的初始化會被 'goto 標籤' 略過|  
|[編譯器警告 (層級 3) C4534](../../error-messages/compiler-warnings/compiler-warning-level-3-c4534.md)|'constructor' 才能 '類別 &#124; struct' 'identifier' 由於預設引數的預設建構函式|  
|[編譯器警告 (層級 3) C4535](../../error-messages/compiler-warnings/compiler-warning-level-3-c4535.md)|呼叫 _set_se_translator() 需要 /EHa|  
|[編譯器警告 (層級 4) C4536](../../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md)|'typename': 類型名稱超出中繼資料 'character_limit' 字元的限制|  
|[編譯器警告 (層級 1) C4537](../../error-messages/compiler-warnings/compiler-warning-level-1-c4537.md)|'object': '。 ' 套用至非 UDT 類型|  
|[編譯器警告 (層級 3) C4538](../../error-messages/compiler-warnings/compiler-warning-level-3-c4538.md)|'type': 不支援此類型的 const/volatile 限定詞|  
|[編譯器警告 (層級 1) C4540](../../error-messages/compiler-warnings/compiler-warning-level-1-c4540.md)|用來將轉換成無法存取或模稜兩可的基底; dynamic_cast執行階段測試將會失敗 ('type1' 到 'type2')|  
|[編譯器警告 (層級 1) C4541](../../error-messages/compiler-warnings/compiler-warning-level-1-c4541.md)|多型類型 'type' /GR-; ' identifier'可能會造成無法預期的行為|  
|編譯器警告 （層級 1） C4542|略過合併插入文字的產生，無法寫入%$M檔案: '%s': %$e|  
|[編譯器警告 (層級 3) C4543](../../error-messages/compiler-warnings/compiler-warning-level-3-c4543.md)|屬性 'no_injected_text' 隱藏插入的文字|  
|[編譯器警告 (層級 1) C4544](../../error-messages/compiler-warnings/compiler-warning-level-1-c4544.md)|'declaration': 預設會忽略這個樣板宣告上的樣板引數|  
|[編譯器警告 (層級 1) C4545](../../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md)|逗號之前的運算式判斷值為遺漏引數清單的函式|  
|[編譯器警告 (層級 1) C4546](../../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md)|逗號之前的函式呼叫遺漏引數清單|  
|[編譯器警告 (層級 1) C4547](../../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md)|'operator': 逗號之前的運算子無效; 必須是具有副作用的運算子|  
|[編譯器警告 (層級 1) C4548](../../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md)|逗號之前的運算式無效; 必須是具有副作用的運算式|  
|[編譯器警告 (層級 1) C4549](../../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md)|'operator': 逗號之前的運算子無效; 您需要 'operator' 嗎?|  
|[編譯器警告 (層級 1) C4550](../../error-messages/compiler-warnings/compiler-warning-level-1-c4550.md)|運算式評估為遺漏引數清單的函式|  
|[編譯器警告 (層級 1) C4551](../../error-messages/compiler-warnings/compiler-warning-level-1-c4551.md)|函式呼叫遺漏引數清單|  
|[編譯器警告 (層級 1) C4552](../../error-messages/compiler-warnings/compiler-warning-level-1-c4552.md)|'operator': 運算子無效;必須是具有副作用的運算子|  
|[編譯器警告 (層級 1) C4553](../../error-messages/compiler-warnings/compiler-warning-level-1-c4553.md)|'operator': 運算子無效;您是否想 ' 運算子？|  
|[編譯器警告 （層級 3） C4554](../../error-messages/compiler-warnings/compiler-warning-level-3-c4554.md) C4554|'operator': 檢查運算子優先順序找出可能發生的錯誤。使用括號釐清順序|  
|[編譯器警告 (層級 1) C4555](../../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md)|運算式無效; 必須是具有副作用的運算式|  
|[編譯器警告 (層級 1) C4556](../../error-messages/compiler-warnings/compiler-warning-level-1-c4556.md)|內建函式直接引數 'value' 的值超出範圍 ' lower_bound-upper_bound'|  
|[編譯器警告 (層級 3) C4557](../../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md)|'__assume' 包含有效的 'effect'|  
|[編譯器警告 (層級 1) C4558](../../error-messages/compiler-warnings/compiler-warning-level-1-c4558.md)|運算元 'value' 的值超出範圍 ' lower_bound-upper_bound'|  
|[編譯器警告 (層級 4) C4559](../../error-messages/compiler-warnings/compiler-warning-level-4-c4559.md)|'function': 重複定義;此函式取得 __declspec(modifier)|  
|[編譯器警告 (層級 1) C4561](../../error-messages/compiler-warnings/compiler-warning-level-1-c4561.md)|'__fastcall' 不具有 '/ /clr' 選項︰ 將轉換成 '\__stdcall'|  
|編譯器警告 （層級 4） C4562|啟用 '/clr' 選項時必須使用完整函式原型: 轉換 '()' 為 '(void)'|  
|[編譯器警告 (層級 4) C4564](../../error-messages/compiler-warnings/compiler-warning-level-4-c4564.md)|方法 'method' 的 'class' 'classname' 定義了不支援的預設參數 'parameter'|  
|[編譯器警告 (層級 4) C4565](../../error-messages/compiler-warnings/compiler-warning-level-4-c4565.md)|'function': 重複定義;__declspec(modifier) 與先前宣告的符號|  
|[編譯器警告 (層級 1) C4566](../../error-messages/compiler-warnings/compiler-warning-level-1-c4566.md)|通用字元名稱 'char' 所代表的字元無法在目前的字碼頁 (%d)|  
|編譯器警告 （層級 1） C4568|'%$S': 沒有任何成員符合明確覆寫的簽章|  
|編譯器警告 （層級 3） C4569|'%$S': 沒有任何成員符合明確覆寫的簽章|  
|[編譯器警告 (層級 3) C4570](../../error-messages/compiler-warnings/compiler-warning-level-3-c4570.md)|'type': 未明確宣告為抽象，但是擁有抽象函式|  
|[編譯器警告 (層級 4) C4571](../../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md)|告知性: catch(...) 語意從 Visual C++ 7.1 開始已經變更，不再攔截結構化例外狀況 (SEH)|  
|[編譯器警告 (層級 1) C4572](../../error-messages/compiler-warnings/compiler-warning-level-1-c4572.md)|[ParamArray] 屬性已被取代下 /clr，使用 '...' 改為|  
|編譯器警告 （層級 1） C4573|'%$S' 的使用需要編譯器擷取 'this'，但目前的預設擷取模式不允許擷取它|  
|編譯器警告 （層級 4） C4574|'Identifier' 定義為 '0': 您是否想要使用 '#if identifier'？|  
|編譯器警告 （層級 1） C4575|'__vectorcall' 不相容的 '/ /clr' 選項︰ 將轉換成 '\__stdcall'|  
|[編譯器警告 (層級 3) C4580](../../error-messages/compiler-warnings/compiler-warning-level-3-c4580.md)|[attribute] 已被取代；請改為指定 System::Attribute 或 Platform::Metadata 作為基底類別|  
|[編譯器警告 (層級 1) C4581](../../error-messages/compiler-warnings/compiler-warning-level-1-c4581.md)|已被取代的行為: '"string"' 取代 'string' 以處理屬性|  
|編譯器警告 （層級 4） C4582|'%$S': 未隱含呼叫建構函式|  
|編譯器警告 （層級 4） C4583|'%$S': 未隱含呼叫解構函式|  
|[編譯器警告 (層級 1) C4584](../../error-messages/compiler-warnings/compiler-warning-level-1-c4584.md)|'class1': 基底類別 'class2' 已經是 '%class3 移' 基底類別|  
|編譯器警告 （層級 1） C4585|'class': WinRT 'public ref class' 必須密封或衍生自現有的未密封類別|  
|編譯器警告 （層級 1） C4586|'%$S': 公用類型不能在名稱為 'Windows' 的最上層命名空間中宣告|  
|編譯器警告 （層級 1） C4587|'anonymous_structure': 行為變更︰ 不再隱含呼叫建構函式|  
|編譯器警告 （層級 1） C4588|'anonymous_structure': 行為變更︰ 不再隱含呼叫解構函式|  
|編譯器警告 （層級 1） C4591|'constexpr' 呼叫深度限制 %d 超過 (/: depth<n>\<數字 >)|  
|編譯器警告 （層級 3） C4592|'function': 'constexpr' 呼叫評估失敗;會在執行階段呼叫函式|  
|編譯器警告 （層級 1） C4593|'function': 'constexpr' 呼叫評估步驟限制 'limit' 超過;使用 /constexpr:\<數字 > 以提高的限制|  
|編譯器警告 （層級 3） C4594|'%$S': 如果擲回例外狀況，則不會隱含呼叫解構函式|  
|編譯器警告 （層級 1） C4595|'%$S': 行為變更: 如果擲回例外狀況，則不會再隱含呼叫解構函式|
