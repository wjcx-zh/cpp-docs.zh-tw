---
title: "Pragma 指示詞和 __Pragma 關鍵字 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- '#pragma'
dev_langs:
- C++
helpviewer_keywords:
- '#pragma directives, C/C++'
- __pragma keyword
- pragma directives, C/C++
- pragmas, C/C++
- preprocessor
- pragmas
- preprocessor, pragmas
- pragma directives (#pragma)
ms.assetid: 9867b438-ac64-4e10-973f-c3955209873f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2ccc6ab8fe90b8b97dee213d65e19eb903249da6
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="pragma-directives-and-the-pragma-keyword"></a>Pragma 指示詞和 __Pragma 關鍵字
Pragma 指示詞會指定電腦專屬或作業專屬的編譯器功能。 Microsoft 編譯器專有的 `__pragma` 關鍵字可讓您在巨集定義範圍內撰寫 pragma 指示詞的程式碼。  
  
## <a name="syntax"></a>語法  
  
```  
  
      #pragma token-string  
__pragma(token-string)  
```  
  
## <a name="remarks"></a>備註  
 C 和 C++ 的每個實作都支援其主機電腦或作業系統獨有的一些功能。 例如，有些程式必須精確掌控放置資料的記憶體區域，或是控制某些函式接收參數的方式。 `#pragma` 指示詞提供了一種方式，讓每個編譯器能夠提供電腦和作業系統專屬功能，同時還能保留與 C 及 C++ 語言的整體相容性。  
  
 Pragma 依定義為電腦或作業系統所專用，對每個編譯器而言通常各不相同。 Pragma 可用於條件陳述式、提供新的前置處理器功能，或是提供實作定義資訊給編譯器。  
  
 `token-string` 是一連串提供特定編譯器指令及引數 (如果有的話) 的字元。 數字符號 (**#**) 的第一個非空格字元必須是包含 pragma 該行; 空白字元可以分隔數字符號和"pragma"這個字。 在 `#pragma` 之後，撰寫轉譯工具可以剖析為前置處理語彙基元的任何文字。 `#pragma` 的引數會受巨集展開的限制。  
  
 如果編譯器發現無法辨識的 pragma，它會發出警告並繼續編譯。  
  
 Microsoft C 和 C++ 編譯器可辨識下列 pragma：  
  
||||  
|-|-|-|  
|[alloc_text](../preprocessor/alloc-text.md)|[auto_inline](../preprocessor/auto-inline.md)|[bss_seg](../preprocessor/bss-seg.md)|  
|[check_stack](../preprocessor/check-stack.md)|[code_seg](../preprocessor/code-seg.md)|[comment](../preprocessor/comment-c-cpp.md)|  
|[component](../preprocessor/component.md)|[conform](../preprocessor/conform.md) <sup>1</sup>|[const_seg](../preprocessor/const-seg.md)|  
|[data_seg](../preprocessor/data-seg.md)|[deprecated](../preprocessor/deprecated-c-cpp.md)|[detect_mismatch](../preprocessor/detect-mismatch.md)|  
|[fenv_access](../preprocessor/fenv-access.md)|[float_control](../preprocessor/float-control.md)|[fp_contract](../preprocessor/fp-contract.md)|  
|[function](../preprocessor/function-c-cpp.md)|[hdrstop](../preprocessor/hdrstop.md)|[include_alias](../preprocessor/include-alias.md)|  
|[init_seg](../preprocessor/init-seg.md) <sup>1</sup>|[inline_depth](../preprocessor/inline-depth.md)|[inline_recursion](../preprocessor/inline-recursion.md)|  
|[intrinsic](../preprocessor/intrinsic.md)|[loop](../preprocessor/loop.md) <sup>1</sup>|[make_public](../preprocessor/make-public.md)|  
|[managed](../preprocessor/managed-unmanaged.md)|[message](../preprocessor/message.md)||  
|[omp](../preprocessor/omp.md)|[once](../preprocessor/once.md)||  
|[optimize](../preprocessor/optimize.md)|[pack](../preprocessor/pack.md)|[pointers_to_members](../preprocessor/pointers-to-members.md) <sup>1</sup>|  
|[pop_macro](../preprocessor/pop-macro.md)|[push_macro](../preprocessor/push-macro.md)|[region、endregion](../preprocessor/region-endregion.md)|  
|[runtime_checks](../preprocessor/runtime-checks.md)|[section](../preprocessor/section.md)|[setlocale](../preprocessor/setlocale.md)|  
|[strict_gs_check](../preprocessor/strict-gs-check.md)|[unmanaged](../preprocessor/managed-unmanaged.md)|[vtordisp](../preprocessor/vtordisp.md) <sup>1</sup>|  
|[warning](../preprocessor/warning.md)|||  
  
 1. 只有 C++ 編譯器支援。  
  
## <a name="pragmas-and-compiler-options"></a>Pragma 和編譯器選項  
 有些 pragma 提供與編譯器選項相同的功能。 當 pragma 在原始程式碼中出現時，它會覆寫編譯器選項指定的行為。 例如，如果您指定[/Zp8](../build/reference/zp-struct-member-alignment.md)，您可以覆寫的程式碼的特定區段的這個編譯器設定[套件](../preprocessor/pack.md):  
  
```  
cl /Zp8 ...  
  
<file> - packing is 8  
// ...  
#pragma pack(push, 1) - packing is now 1  
// ...  
#pragma pack(pop) - packing is 8  
</file>  
```  
  
## <a name="the-pragma-keyword"></a>__pragma() 關鍵字  
 **Microsoft specific**  
  
 編譯器也支援 `__pragma` 關鍵字，其功能與 `#pragma` 指示詞相同，但是可以在巨集定義中以內嵌方式使用。 `#pragma`無法在巨集定義中使用指示詞，因為編譯器會將數字符號字元 （' #'） 解譯為指示詞中[字串化運算子 （#）](../preprocessor/stringizing-operator-hash.md)。  
  
 下列程式碼範例將示範如何在巨集中使用 `__pragma` 關鍵字。 這段程式碼摘錄自＜編譯器 COM 支援範例＞中 ACDUAL 範本的 mfcdual.h 標頭：  
  
```  
#define CATCH_ALL_DUAL \  
CATCH(COleException, e) \  
{ \  
_hr = e->m_sc; \  
} \  
AND_CATCH_ALL(e) \  
{ \  
__pragma(warning(push)) \  
__pragma(warning(disable:6246)) /*disable _ctlState prefast warning*/ \  
AFX_MANAGE_STATE(pThis->m_pModuleState); \  
__pragma(warning(pop)) \  
_hr = DualHandleException(_riidSource, e); \  
} \  
END_CATCH_ALL \  
return _hr; \  
```  
  
 **End Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [C/c + + 前置處理器參考](../preprocessor/c-cpp-preprocessor-reference.md)   
 [C Pragma](../c-language/c-pragmas.md)   
 [關鍵字](../cpp/keywords-cpp.md)