---
title: "編譯器警告 C4000 透過 C4199 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4000
- C4002
- C4006
- C4008
- C4019
- C4023
- C4025
- C4026
- C4027
- C4030
- C4033
- C4035
- C4036
- C4038
- C4041
- C4045
- C4051
- C4052
- C4053
- C4057
- C4060
- C4063
- C4064
- C4065
- C4066
- C4068
- C4069
- C4075
- C4076
- C4077
- C4080
- C4081
- C4085
- C4086
- C4087
- C4097
- C4102
- C4109
- C4112
- C4115
- C4117
- C4119
- C4120
- C4122
- C4123
- C4125
- C4130
- C4131
- C4132
- C4137
- C4138
- C4141
- C4143
- C4145
- C4152
- C4153
- C4155
- C4158
- C4160
- C4161
- C4163
- C4164
- C4165
- C4166
- C4167
- C4168
- C4174
- C4175
- C4176
- C4177
- C4178
- C4179
- C4180
- C4181
- C4182
- C4185
- C4186
- C4187
- C4188
- C4189
- C4191
- C4193
- C4194
- C4195
- C4196
- C4199
dev_langs:
- C++
ms.assetid: 426f495a-43af-4906-ad2b-6e5822c09965
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 4bac7b2942f9d72674b8092dc7bf64174dd3c349
ms.openlocfilehash: 9e7f0c939f5260991d18b69fc8965e1073bff406
ms.lasthandoff: 04/24/2017

---
# <a name="compiler-warnings-c4000-through-c4199"></a>編譯器警告 C4000 透過 C4199
這一部分的文件中的文章包含 Visual c + + 編譯器警告的資訊子集。 您可以在此存取資訊或在**輸出**視窗在 Visual Studio 中，您可以選取警告代碼，然後選擇 F1 鍵。  
  
> [!NOTE]
>  並非每個[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]錯誤或警告會記載於 MSDN 中。 在許多情況下，診斷訊息會提供所有可用的資訊。 如果您認為錯誤訊息需要補充說明，請告訴我們。 您可以使用這個頁面上的回函表單或移至 Visual Studio 中的功能表列並選擇**協助**，**回報 Bug**，或您可以提出建議或 bug 報告上[Microsoft Connect](http://connect.microsoft.com/VisualStudio)。  
  
 您可能會發現其他協助的 MSDN 公共論壇上錯誤及警告。 [Visual c + + 語言](http://go.microsoft.com/fwlink/?LinkId=158195)論壇是關於問題及討論[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]語言語法和編譯器。 [Visual c + + 一般](http://go.microsoft.com/fwlink/?LinkId=158194)論壇是關於問題[!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)]其他論壇中沒有討論之。 您也可能會在找到關於錯誤和警告的說明[堆疊溢位](http://stackoverflow.com/)。  
  
## <a name="in-this-section"></a>本章節內容  
  
|警告|訊息|  
|-------------|-------------|  
|編譯器警告 C4000|未知的警告<br /><br /> 請選擇 Visual c + + 的技術支援 命令<br /><br /> [說明] 功能表，或開啟技術支援說明檔，如需詳細資訊|  
|[編譯器警告 (層級 4) C4001](../../error-messages/compiler-warnings/compiler-warning-level-4-c4001.md)|使用單行註解，ANSI C 標準不支援|  
|編譯器警告 （層級 1） C4002|巨集 'identifier' 的實質參數太多|  
|[編譯器警告 (層級 1) C4003](../../error-messages/compiler-warnings/compiler-warning-level-1-c4003.md)|巨集 'identifier' 的實質參數不足|  
|[編譯器警告 (層級 1) C4005](../../error-messages/compiler-warnings/compiler-warning-level-1-c4005.md)|'identifier': 巨集重新定義|  
|編譯器警告 （層級 1） C4006|#undef 必須是識別項|  
|[編譯器警告 (層級 2) C4007](../../error-messages/compiler-warnings/compiler-warning-level-2-c4007.md)|'function': 必須是 '屬性'|  
|編譯器警告 （層級 3） C4008|'function': 已略過 '屬性' 屬性|  
|[編譯器警告 (層級 1) C4010](../../error-messages/compiler-warnings/compiler-warning-level-1-c4010.md)|單行註解包含行接續字元|  
|[編譯器警告 (層級 3) C4013](../../error-messages/compiler-warnings/compiler-warning-level-3-c4013.md)|' function' 未定義。假設 extern 傳回整數|  
|[編譯器警告 (層級 1) C4015](../../error-messages/compiler-warnings/compiler-warning-level-1-c4015.md)|'識別碼': 位元欄位的類型必須是整數類資料|  
|[編譯器警告 (層級 3) C4018](../../error-messages/compiler-warnings/compiler-warning-level-3-c4018.md)|'expression': signed/unsigned 不相符|  
|編譯器警告 （層級 4） C4019|在全域範圍有空的陳述式|  
|[編譯器警告 (層級 1) C4020](../../error-messages/compiler-warnings/compiler-warning-level-1-c4020.md)|'function': 實質參數太多|  
|[編譯器警告 (層級 1) C4022](../../error-messages/compiler-warnings/compiler-warning-level-1-c4022.md)|'function': 指標不相符，實際的參數 'parameter number'|  
|編譯器警告 （層級 1） C4023|'function': 基底的指標傳遞至沒有原型的函式︰ 參數 'parameter_number'|  
|[編譯器警告 (層級 1) C4024](../../error-messages/compiler-warnings/compiler-warning-level-1-c4024.md)|'function': 型式和實質參數 'parameter_number' 不同的類型|  
|編譯器警告 （層級 1） C4025|'function': 基底的指標傳遞至具有變數引數的函式︰ 參數 'parameter_number'|  
|編譯器警告 （層級 1） C4026|宣告有型式參數清單的函式|  
|編譯器警告 （層級 1） C4027|宣告沒有型式參數清單的函式|  
|[編譯器警告 （層級 1） C4028](../../error-messages/compiler-warnings/compiler-warning-level-1-c4028.md)8|型式參數 'parameter_number' 與宣告不同|  
|[編譯器警告 (層級 1) C4029](../../error-messages/compiler-warnings/compiler-warning-level-1-c4029.md)|在函式宣告和函式定義中的型式參數清單不同|  
|編譯器警告 （層級 1） C4030|第一型式參數清單比第二清單長|  
|[編譯器警告 (層級 1) C4031](../../error-messages/compiler-warnings/compiler-warning-level-1-c4031.md)|第二型式參數清單比第一清單長|  
|[編譯器警告 (層級 4) C4032](../../error-messages/compiler-warnings/compiler-warning-level-4-c4032.md)|型式參數 'parameter_number' 有不同的類型，當升級|  
|編譯器警告 （層級 1） C4033|'function' 必須傳回值|  
|[編譯器警告 (層級 1) C4034](../../error-messages/compiler-warnings/compiler-warning-level-1-c4034.md)|sizeof 傳回 0|  
|編譯器警告 （層級 3） C4035|'function': 沒有傳回值|  
|編譯器警告 （層級 1） C4036|未命名的 'type' 當做實質參數|  
|編譯器警告 （層級 1） C4038|'modifier': 不合法的類別修飾詞|  
|編譯器警告 （層級 1） C4041|編譯器限制: 瀏覽器資訊超出編譯器上限，已終止輸出|  
|[編譯器警告 (層級 1) C4042](../../error-messages/compiler-warnings/compiler-warning-level-1-c4042.md)|'identifier': 具有錯誤的儲存類別|  
|編譯器警告 （層級 1） C4045|'array': 陣列界限溢位|  
|[編譯器警告 (層級 1) C4047](../../error-messages/compiler-warnings/compiler-warning-level-1-c4047.md)|'operator': 'identifier1' 在間接取值上與 'identifier2' 的層級不同|  
|[編譯器警告 (層級 1) C4048](../../error-messages/compiler-warnings/compiler-warning-level-1-c4048.md)|不同的陣列註標: 'identifier1' 和 'identifier2'|  
|[編譯器警告 (層級 1) C4049](../../error-messages/compiler-warnings/compiler-warning-level-1-c4049.md)|編譯器限制: 程式碼行數超過上限，已終止發出行號|  
|編譯器警告 （層級 1） C4051|轉換類型，可能導致資料遺失|  
|編譯器警告 （層級 4） C4052|函式宣告不同; 一個包含變數引數|  
|編譯器警告 （層級 4） C4053|'?:' 有一類型為 void 的運算元|  
|[編譯器警告 (層級 2) C4056](../../error-messages/compiler-warnings/compiler-warning-level-2-c4056.md)|在浮點常數算術中溢位|  
|編譯器警告 （層級 4） C4057|'operator': 'identifier1' 在間接取值和至不同基底類型有些許不同於 'identifier2'|  
|編譯器警告 C4060|switch 陳述式沒有包含 'case' 或 'default' 標籤|  
|[編譯器警告 (層級 4) C4061](../../error-messages/compiler-warnings/compiler-warning-level-4-c4061.md)|case 標籤並未明確處理列舉程式 'identifier' 中參數的列舉 'enumeration'|  
|[編譯器警告 (層級 4) C4062](../../error-messages/compiler-warnings/compiler-warning-level-4-c4062.md)|在列舉 'enumeration' 的 switch 中未處理列舉程式 'identifier'|  
|編譯器警告 c4063:|case 'identifier' 不是列舉的有效 'enumeration' 的參數值|  
|編譯器警告 C4064|不完整列舉 'enumeration' 的參數|  
|編譯器警告 C4065|switch 陳述式包含 'default'，但沒有 'case' 標籤|  
|編譯器警告 （層級 3） C4066|忽略超出寬字元常數中第一個的字元|  
|[編譯器警告 (層級 1) C4067](../../error-messages/compiler-warnings/compiler-warning-level-1-c4067.md)|未預期的語彙基元，接著前置處理器指示詞 - 必須是新行|  
|編譯器警告 （層級 1） C4068|未知的 pragma|  
|編譯器警告 C4069|長雙精度浮點數與l雙精度浮點數的精確度相同|  
|[編譯器警告 (層級 3) C4073](../../error-messages/compiler-warnings/compiler-warning-level-3-c4073.md)|初始設定式置於程式庫初始化區域|  
|[編譯器警告 (層級 1) C4074](../../error-messages/compiler-warnings/compiler-warning-level-1-c4074.md)|初始設定式置於編譯器保留的初始化區域|  
|編譯器警告 （層級 1） C4075|初始設定式置於無法辨識的初始化區域|  
|編譯器警告 （層級 1） C4076|'type_modifier': 不能與類型 'typename'|  
|編譯器警告 （層級 1） C4077|未知的 check_stack 選項|  
|[編譯器警告 (層級 1) C4079](../../error-messages/compiler-warnings/compiler-warning-level-1-c4079.md)|未預期的語彙基元 'token'|  
|編譯器警告 （層級 1） C4080|必須是區段名稱的識別項，但卻找到 'symbol'|  
|編譯器警告 （層級 1） C4081|必須是 'token1'; 但找到 'token2'|  
|[編譯器警告 (層級 1) C4083](../../error-messages/compiler-warnings/compiler-warning-level-1-c4083.md)|必須是 'token';找到識別項 'identifier'|  
|編譯器警告 （層級 1） C4085|pragma 參數必須為 'on' 或 'off'|  
|編譯器警告 （層級 1） C4086|pragma 參數必須為 '1'、'2'、'4'、'8' 或 '16'|  
|編譯器警告 （層級 1） C4087|'function': 搭配 'void' 參數清單宣告|  
|[編譯器警告 (層級 1) C4088](../../error-messages/compiler-warnings/compiler-warning-level-1-c4088.md)|'function': 實質參數 'parameter_number'，型式參數 'parameter_number' 中的指標不相符|  
|[編譯器警告 (層級 1) C4089](../../error-messages/compiler-warnings/compiler-warning-level-1-c4089.md)|'function': 實質參數 'parameter_number'，型式參數 'parameter_number' 中的不同類型|  
|[編譯器警告 (層級 1) C4090](../../error-messages/compiler-warnings/compiler-warning-level-1-c4090.md)|'operation': 不同 '修飾詞' 限定詞|  
|[編譯器警告 (層級 1) C4091](../../error-messages/compiler-warnings/compiler-warning-level-1-c4091.md)|關鍵字 ': 未不宣告任何變數時，忽略 'type' 的左邊|  
|[編譯器警告 (層級 4) C4092](../../error-messages/compiler-warnings/compiler-warning-level-4-c4092.md)|sizeof 傳回 'unsigned long'|  
|[編譯器警告 (層級 2) C4094](../../error-messages/compiler-warnings/compiler-warning-level-2-c4094.md)|未標記 ' token' 宣告沒有符號|  
|[編譯器警告 (層級 1) C4096](../../error-messages/compiler-warnings/compiler-warning-level-1-c4096.md)|'identifier': 介面不是 COM 介面。將不會發出到 IDL|  
|編譯器警告 （層級 1） C4097|pragma 參數必須為 'restore' 或 'off'|  
|[編譯器警告 (層級 1) C4098](../../error-messages/compiler-warnings/compiler-warning-level-1-c4098.md)|'function': 'void' 傳回值的函式|  
|[編譯器警告 (層級 2) C4099](../../error-messages/compiler-warnings/compiler-warning-level-2-c4099.md)|'identifier': 第一個看到使用 'object_type1' 現在發現使用 'object_type2' 的型別名稱|  
|[編譯器警告 (層級 4) C4100](../../error-messages/compiler-warnings/compiler-warning-level-4-c4100.md)|'identifier': 未參考的型式參數|  
|[編譯器警告 (層級 3) C4101](../../error-messages/compiler-warnings/compiler-warning-level-3-c4101.md)|'identifier': 未參考的區域變數|  
|編譯器警告 （層級 3） C4102|'label': 未參考的標籤|  
|[編譯器警告 (層級 1) C4103](../../error-messages/compiler-warnings/compiler-warning-level-1-c4103.md)|'filename': 對齊之後包含標頭，變更可能是因為缺少 #pragma pack(pop)|  
|編譯器警告 （層級 1） C4109|未預期的識別項 'identifier'|  
|編譯器警告 （層級 1） C4112|#行需要 1 到 'line_count' 之間的整數|  
|[編譯器警告 (層級 1) C4113](../../error-messages/compiler-warnings/compiler-warning-level-1-c4113.md)|'identifier1' 在不同於 'identifier2' 的參數清單中|  
|[編譯器警告 (層級 1) C4114](../../error-messages/compiler-warnings/compiler-warning-level-1-c4114.md)|相同類型的限定詞已經使用多次|  
|編譯器警告 （層級 1 和層級 4） C4115|'type': 命名括號括住的類型定義|  
|[編譯器警告 (層級 1) C4116](../../error-messages/compiler-warnings/compiler-warning-level-1-c4116.md)|括號運算式中定義了未命名的類型。|  
|編譯器警告 （層級 1） C4117|巨集名稱 'name' 為保留名稱，忽略 'command'|  
|編譯器警告 （層級 1） C4119|指定的基底 'base1' 和 'base2' 不同|  
|編譯器警告 （層級 1） C4120|兩者分別為基底與非基底，無法轉換|  
|[編譯器警告 (層級 4) C4121](../../error-messages/compiler-warnings/compiler-warning-level-4-c4121.md)|'symbol': 成員的對齊方式已受 pack 影響|  
|編譯器警告 （層級 1） C4122|'function': alloc_text 僅適用使用 C 連結的函式|  
|編譯器警告 （層級 1） C4123|指定不同的基底運算式|  
|[編譯器警告 (層級 1) C4124](../../error-messages/compiler-warnings/compiler-warning-level-1-c4124.md)|__fastcall 與堆疊檢查並用會降低執行效能|  
|編譯器警告 （層級 4） C4125|八進位逸出序列結尾有十進位數字|  
|[編譯器警告 (層級 4) C4127](../../error-messages/compiler-warnings/compiler-warning-level-4-c4127.md)|條件運算式是常數|  
|[編譯器警告 (層級 1) C4129](../../error-messages/compiler-warnings/compiler-warning-level-1-c4129.md)|'character': 無法辨識的字元逸出序列|  
|編譯器警告 （層級 4） C4130|'operator': 字串常數的位址進行邏輯運算|  
|編譯器警告 （層級 4） C4131|'function': 使用舊樣式的宣告子|  
|編譯器警告 （層級 4） C4132|'object': 應初始化常數物件|  
|[編譯器警告 (層級 3) C4133](../../error-messages/compiler-warnings/compiler-warning-level-3-c4133.md)|'expression': 不相容的類型-'type1' 到 'type2'|  
|編譯器警告 C4137|'function': 沒有來自浮點函式的傳回值|  
|編譯器警告 （層級 1） C4138|在註解外部找到 '*/'|  
|編譯器警告 （層級 1） C4141|'modifier': 使用超過一次|  
|[編譯器警告 (層級 1) C4142](../../error-messages/compiler-warnings/compiler-warning-level-1-c4142.md)|良性的類型重複定義|  
|編譯器警告 （層級 1） C4143|pragma 'same_seg' 不支援; 使用 __based 配置|  
|[編譯器警告 (層級 1) C4144](../../error-messages/compiler-warnings/compiler-warning-level-1-c4144.md)|'expression': 關聯運算式做為 switch 運算式|  
|編譯器警告 （層級 1） C4145|'expression1': 關聯運算式做為 switch 運算式;可能與 'expression2' 混淆|  
|[編譯器警告 (層級 2) C4146](../../error-messages/compiler-warnings/compiler-warning-level-2-c4146.md)|一元減號運算子套用 unsigned 類型，所得的結果也會是 unsigned 類型|  
|[編譯器警告 (層級 2) C4150](../../error-messages/compiler-warnings/compiler-warning-level-2-c4150.md)|刪除的指標不完整類型 'type';呼叫沒有解構函式|  
|編譯器警告 （層級 4） C4152|非標準的擴充，運算式中函式/資料的指標轉換|  
|編譯器警告 （層級 1） C4153|運算式中函式/資料的指標轉換|  
|[編譯器警告 (層級 1) C4154](../../error-messages/compiler-warnings/compiler-warning-level-1-c4154.md)|不能在陣列運算式上使用 delete; 所以將陣列轉換成指標|  
|編譯器警告 （層級 1） C4155|刪除陣列運算式沒有使用陣列形式的 'delete'|  
|[編譯器警告 (層級 2) C4156](../../error-messages/compiler-warnings/compiler-warning-level-2-c4156.md)|刪除陣列運算式沒有使用陣列形式的 'delete'; 改用陣列形式|  
|[編譯器警告 (層級 1) C4157](../../error-messages/compiler-warnings/compiler-warning-level-1-c4157.md)|C 編譯器忽略 pragma|  
|編譯器警告 （層級 1） C4158|假設 #pragma pointers_to_members （full_generality，'inheritance_type'）|  
|[編譯器警告 (層級 3) C4159](../../error-messages/compiler-warnings/compiler-warning-level-3-c4159.md)|#pragma ' pragma'(pop,...)︰ 已經推出之前推入的識別項 'identifier'|  
|編譯器警告 （層級 1） C4160|#pragma ' pragma'(pop,...)︰ 未發現之前推入的識別項 'identifier'|  
|編譯器警告 （層級 3） C4161|#pragma ' pragma'(pop...): pop|  
|[編譯器警告 (層級 1) C4162](../../error-messages/compiler-warnings/compiler-warning-level-1-c4162.md)|'identifier': 使用 C 連結，找到的函式|  
|編譯器警告 （層級 1） C4163|'identifier': 無法當做內建函式的函式|  
|編譯器警告 （層級 1） C4164|'function': 未宣告的內建函式|  
|編譯器警告 （層級 1） C4165|將 'HRESULT' 轉換為 'bool'; 您確定這是您要的?|  
|編譯器警告 （層級 1） C4166|對建構函式/解構函式的不合法呼叫慣例|  
|編譯器警告 （層級 1） C4167|'function': 只能為內建函式|  
|編譯器警告 （層級 1） C4168|編譯器限制︰ 偵錯工具類型不足，刪除程式資料庫 'database' 並重建|  
|[編譯器警告 (層級 1) C4172](../../error-messages/compiler-warnings/compiler-warning-level-1-c4172.md)|傳回區域變數或暫存的位址|  
|編譯器警告 （層級 1） C4174|'name': 無法當做 #pragma 元件|  
|編譯器警告 （層級 1） C4175|#pragma component(browser, on)︰ 必須在命令列上指定瀏覽器資訊|  
|編譯器警告 （層級 1） C4176|'subcomponent': #pragma 元件瀏覽器的未知子元件|  
|編譯器警告 （層級 1） C4177|#pragma 'pragma' 只能在全域範圍或命名空間範圍|  
|編譯器警告 （層級 1） C4178|對 switch 運算式的類型而言，case 常數 'constant' 太大|  
|編譯器警告 （層級 4） C4179|'/ / *': 剖析為 '/' 和' /\*': 標準混淆 ' / /' 註解|  
|編譯器警告 （層級 1） C4180|套用至函式類型的限定詞沒有意義; 已忽略|  
|編譯器警告 C4181|套用至參考類型的限定詞; 已忽略|  
|編譯器警告 （層級 1） C4182|#包含巢狀層級為 'nest_count' 深層;可能有無限遞迴|  
|[編譯器警告 (層級 1) C4183](../../error-messages/compiler-warnings/compiler-warning-level-1-c4183.md)|'identifier': 遺漏傳回類型;假設為傳回 'int' 的成員函式|  
|編譯器警告 （層級 1） C4185|忽略未知的 #import 屬性 'attribute'|  
|編譯器警告 （層級 1） C4186|#匯入屬性 'attribute' 需要 'argument_count' 引數。忽略|  
|編譯器警告 （層級 1） C4187|#匯入的屬性 'attribute1' 和 'attribute2' 不相容。兩者都已忽略|  
|編譯器警告 （層級 1） C4188|常數運算式不是整數，不能在這裡使用|  
|編譯器警告 （層級 4） C4189|'identifier': 已初始化區域變數，但並未參考|  
|[編譯器警告 (層級 1) C4190](../../error-messages/compiler-warnings/compiler-warning-level-1-c4190.md)|'identifier1' 具有 C 連結指定，但傳回 UDT 與 C 不相容的 ' identifier2'|  
|編譯器警告 （層級 3） C4191|' 運算子/operation ': 從 'type_of_expression' 不安全的轉換至 'type_required' \nCalling 透過結果指標此函式可能會造成您的程式失敗|  
|[編譯器警告 (層級 3) C4192](../../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md)|會自動匯入類型程式庫 'library' 時排除 'identifier'|  
|編譯器警告 （層級 3） C4193|#pragma warning （pop): 不符合 '#pragma warning （push)'|  
|編譯器警告 （層級 1） C4194|#不可為巢狀 pragma start_map_region;忽略|  
|編譯器警告 （層級 1） C4195|#pragma stop_map_region 但不比對 #pragma start_map_region; 使用忽略|  
|編譯器警告 （層級 1） C4196|必須是 '%$L' 或 '%$L'; 找到 '%$L'|  
|[編譯器警告 (層級 3) C4197](../../error-messages/compiler-warnings/compiler-warning-level-3-c4197.md)|'type': 類型轉換中的最上層 volatile 會被忽略|  
|編譯器警告 （層級 1、 層級 2、 level 3、 和層級 4） C4199|%s|
