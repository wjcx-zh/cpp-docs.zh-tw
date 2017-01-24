---
title: "預設為關閉的編譯器警告 | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "cl.exe 編譯器, 設定選項"
  - "警告, 編譯器"
ms.assetid: 69809cfb-a38a-4035-b154-283a61938df8
caps.latest.revision: 39
caps.handback.revision: 37
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 預設為關閉的編譯器警告
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

編譯器包含預設為關閉的警告，因為大多數的使用者不想看到它們。  不過，您可以使用下列其中一個選項啟用這類警告。  
  
 `#pragma warning(default :`  `warning_number` `)`  
 指定的警告 \(`warning_number`\) 會在其預設層級上啟用。  警告的文件包含警告的預設層級。  
  
 `#pragma warning(` `warning_level`  `:`  `warning_number` `)`  
 指定的警告 \(`warning_number`\) 會在指定的層級 \(`warning_level`\) 上啟用。  
  
 [\/Wall](../build/reference/compiler-option-warning-level.md)  
 **\/Wall** 會啟用所有預設停用的警告。  
  
 根據預設，下列警告會關閉。  
  
|||  
|-|-|  
|[C4061](../error-messages/compiler-warnings/compiler-warning-level-4-c4061.md) \(層級 4\)|在列舉 'enumeration' 的 switch 中，case 標籤並未明確處理列舉值 'identifier'|  
|[C4062](../error-messages/compiler-warnings/compiler-warning-level-4-c4062.md) \(層級 3\)|在列舉 'enumeration' 的 switch 中未明確處理列舉值 'identifier'|  
|C4191 \(層級 3\)|'operator\/operation': 從 'type of expression' 到 'type required' 不安全的轉換|  
|[C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) \(層級 4\)|'identifier': 將 'type1' 轉換為 'type2'，資料可能遺失|  
|[C4254](../error-messages/compiler-warnings/compiler-warning-level-4-c4254.md) \(層級 4\)|'operator': 將 'type1' 轉換為 'type2'，資料可能遺失|  
|[C4255](../error-messages/compiler-warnings/compiler-warning-level-4-c4255.md) \(層級 4\)|'function': 未提供函式原型：將 '\(\)' 轉換為 '\(void\)'|  
|[C4263](../error-messages/compiler-warnings/compiler-warning-level-4-c4263.md) \(層級 4\)|'function': 成員函式不覆寫任何基底類別虛擬成員的函式|  
|[C4264](../error-messages/compiler-warnings/compiler-warning-level-1-c4264.md) \(層級 1\)|'virtual\_function': 基底類別 'class' 的虛擬成員函式沒有覆寫; 函式已隱藏|  
|[C4265](../error-messages/compiler-warnings/compiler-warning-level-3-c4265.md) \(層級 3\)|'class': 類別有虛擬函式，但解構函式不是虛擬的|  
|[C4266](../error-messages/compiler-warnings/compiler-warning-level-4-c4266.md) \(層級 4\)|'function': 基底類別 'type' 的虛擬成員函式沒有覆寫; 函式已隱藏|  
|[C4287](../error-messages/compiler-warnings/compiler-warning-level-3-c4287.md) \(層級 3\)|'operator': 不帶正負號\/負常數不相符|  
|[C4289](../error-messages/compiler-warnings/compiler-warning-level-4-c4289.md) \(層級 4\)|使用非標準的擴充：'var' : 在 for\-loop 範圍外使用 for\-loop 中所宣告的迴圈控制變數|  
|[C4296](../error-messages/compiler-warnings/compiler-warning-level-4-c4296.md) \(層級 4\)|'operator': 運算式永遠是 false|  
|[C4302](../error-messages/compiler-warnings/compiler-warning-level-2-c4302.md) \(層級 2\)|'conversion': 從 'type1' 到 'type2' 發生截斷狀況|  
|[C4311](../error-messages/compiler-warnings/compiler-warning-level-1-c4311.md) \(層級 1\)|'variable' : 指標從 'type' 到 'type' 截斷|  
|[C4312](../error-messages/compiler-warnings/compiler-warning-level-1-c4312.md) \(層級 1\)|'operation' : 將 'type1' 轉換為較大的 'type2'|  
|[C4339](../error-messages/compiler-warnings/compiler-warning-level-4-c4339.md) \(層級 4\)|'type' : 偵測到在 CLR 中繼資料中使用未定義的類型 \- 使用此類型可能造成執行階段例外狀況|  
|[C4342](../error-messages/compiler-warnings/compiler-warning-level-1-c4342.md) \(層級 1\)|行為變更: 呼叫了 'function'，但是先前版本中呼叫的是成員運算子|  
|[C4350](../error-messages/compiler-warnings/compiler-warning-level-1-c4350.md) \(層級 1\)|行為變更: 呼叫了 'member1' 而不是 'member2'|  
|[C4355](../error-messages/compiler-warnings/compiler-warning-c4355.md)|'this' : 在基底成員初始設定式清單中使用|  
|[C4365](../error-messages/compiler-warnings/compiler-warning-level-4-c4365.md) \(層級 4\)|'action': 從 'type\_1' 轉換為 'type\_2'，signed\/unsigned 不相符|  
|C4370 \(層級 3\)|因為較佳的封裝，類別配置已從舊版的編譯器變更|  
|C4371 \(層級 3\)|因為可提供較佳的成員 'member' 封裝，類別配置可能已從舊版的編譯器變更|  
|C4388 \(層級 4\)|帶正負號\/不帶正負號不相符|  
|[C4412](../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md) \(層級 2\)|'function': 函式簽章含有類型 'type'，C\+\+ 物件在純程式碼與混合或機器碼之間傳遞並不安全|  
|[C4431](../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md) \(層級 4\)|遺漏類型規範 \- 假設為 int。  注意: C 已不再支援 default\-int|  
|[C4435](../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md) \(層級 4\)|'class1' : \/vd2 底下的物件配置將因虛擬基底 'class2' 而變更|  
|[C4437](../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md) \(層級 4\)|從虛擬基底 'class1' 到 'class2' 的 dynamic\_cast 在某些內容中可能會失敗|  
|C4444 \(層級 3\)|此內容未實作最上層的 '\_\_unaligned'|  
|C4471 \(層級 4\)|不限範圍的列舉之向前宣告必須含有基礎類型 \(假設是 int\)|  
|C4472 \(層級 1\)|'identifier' 是原生列舉：新增存取規範 \(private\/public\) 以便宣告 Managed 列舉|  
|[C4514](../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md) \(層級 4\)|'function': 已移除未參考的內嵌函式|  
|[C4536](../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md) \(層級 4\)|'type name': 類型名稱超出中繼資料 'limit' 個字元的限制|  
|[C4545](../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md) \(層級 1\)|逗號之前的運算式判斷值為遺漏引數清單的函式|  
|[C4546](../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md) \(層級 1\)|逗號之前的函式呼叫遺漏引數清單|  
|[C4547](../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md) \(層級 1\)|'operator': 逗號之前的運算子無效; 必須是具有副作用的運算子|  
|[C4548](../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md) \(層級 1\)|逗號之前的運算式無效; 必須是具有副作用的運算式|  
|[C4549](../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md) \(層級 1\)|'operator': 逗號之前的運算子無效; 您需要 'operator' 嗎?|  
|[C4555](../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md) \(層級 1\)|運算式無效; 必須是具有副作用的運算式|  
|[C4557](../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md) \(層級 3\)|'\_\_assume' 包含有效的 'effect'|  
|[C4571](../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md) \(層級 4\)|告知性：catch\(…\) 語意 \(Semantics\) 從 Visual C\+\+ 7.1 開始已經變更，不再攔截結構化例外狀況處理常式 \(SEH\)|  
|C4574 \(層級 4\)|'identifier' 定義為 '0'：您是指使用 '\#if identifier' 嗎？|  
|C4608 \(層級 3\)|'symbol1' 已由初始設定式清單 'symbol2' 中的其他等位成員初始化|  
|[C4619](../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md) \(層級 3\)|\#pragma warning: 警告編號 'number' 不存在|  
|[C4623](../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md) \(層級 4\)|'derived class': 因為無法存取基底類別預設建構函式，所以無法產生預設建構函式|  
|[C4625](../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md) \(層級 4\)|'derived class': 因為無法存取基底類別複製建構函式，所以無法產生複製建構函式|  
|[C4626](../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md) \(層級 4\)|'derived class': 因為無法存取基底類別的指派運算子，所以無法產生指派運算子|  
|[C4628](../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md) \(層級 1\)|不支援使用 \-Ze 的雙拼詞。  字元順序 'digraph' 沒有解譯為 'char' 的替代語彙基元 \(Token\)|  
|[C4640](../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md) \(層級 3\)|'instance': 區域靜態物件的建構不是安全執行緒|  
|[C4668](../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md) \(層級 4\)|'symbol' 未定義成前置處理器巨集，以 '0' 取代 'directives'|  
|C4682 \(層級 4\)|'symbol'：沒有指定方向參數屬性，預設為 \[in\]|  
|[C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md) \(層級 3\)|'user\-defined type': 行為可能有變更，在 UDT 傳回呼叫慣例中發生變更|  
|[C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) \(層級 1\)|'function'：非私用成員的簽章含有組件私用原生類型 'native\_type'|  
|[C4710](../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md) \(層級 4\)|'function': 未內嵌函式|  
|[C4738](../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md) \(層級 3\)|在記憶體中儲存 32 位元浮點結果，可能會損失效能|  
|C4767 \(層級 4\)|區段名稱 'symbol' 超過 8 個字元，將由連結器截斷|  
|C4786 \(層級 3\)|'symbol'：物件名稱被截斷成 'number' 個字元 \(在偵錯資訊中\)|  
|[C4820](../error-messages/compiler-warnings/compiler-warning-level-4-c4820.md) \(層級 4\)|在成員建構 'member\_name' 之後加入 'bytes' 位元組填補|  
|[C4826](../error-messages/compiler-warnings/compiler-warning-level-2-c4826.md) \(層級 2\)|從 'type1' 至 'type2' 的轉換是 sign\-extended。  這可能會造成未預期的執行階段行為|  
|[C4837](../error-messages/compiler-warnings/compiler-warning-level-4-c4837.md) \(層級 4\)|偵測到三併詞: '??%c' 已由 '%c' 取代|  
|[C4905](../error-messages/compiler-warnings/compiler-warning-level-1-c4905.md) \(層級 1\)|寬字串常值轉換成 'LPSTR'|  
|[C4906](../error-messages/compiler-warnings/compiler-warning-level-1-c4906.md) \(層級 1\)|字串常值轉換成 'LPWSTR'|  
|[C4917](../error-messages/compiler-warnings/compiler-warning-level-1-c4917.md) \(層級 1\)|'declarator': GUID 僅能與類別、介面或命名空間產生關聯|  
|[C4928](../error-messages/compiler-warnings/compiler-warning-level-1-c4928.md) \(層級 1\)|不合法的 copy\-initialization; 已經隱含套用一個以上的使用者定義的轉換|  
|[C4931](../error-messages/compiler-warnings/compiler-warning-level-4-c4931.md) \(層級 4\)|我們假設已針對 number 位元指標建置類型程式庫|  
|[C4946](../error-messages/compiler-warnings/compiler-warning-level-1-c4946.md) \(層級 1\)|在關聯的類別之間使用的 reinterpret\_cast：'class1' 和 'class2'|  
|C4962|'function': 特性指引最佳化已停用，因為最佳化導致分析資料變成不一致|  
|[C4986](../error-messages/compiler-warnings/compiler-warning-c4986.md) \(層級 4\)|'symbol'：例外狀況規格與上一個宣告不符|  
|C4987 \(層級 4\)|使用非標準的擴充：'throw \(...\)'|  
|C4988 \(層級 4\)|'symbol'：變數已在類別\/函式範圍外宣告|  
  
## 請參閱  
 [warning](../preprocessor/warning.md)