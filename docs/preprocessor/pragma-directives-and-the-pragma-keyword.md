---
title: "Pragma 指示詞和 __Pragma 關鍵字 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "#pragma"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#pragma 指示詞, C/C++"
  - "__pragma 關鍵字"
  - "pragma 指示詞 (#pragma)"
  - "pragma 指示詞, C/C++"
  - "Pragma"
  - "Pragma, C/C++"
  - "前置處理器"
  - "前置處理器, Pragma"
ms.assetid: 9867b438-ac64-4e10-973f-c3955209873f
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Pragma 指示詞和 __Pragma 關鍵字
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Pragma 指示詞會指定電腦專屬或作業專屬的編譯器功能。  Microsoft 編譯器專有的 `__pragma` 關鍵字可讓您在巨集定義範圍內撰寫 pragma 指示詞的程式碼。  
  
## 語法  
  
```  
  
      #pragma token-string  
__pragma(token-string)  
```  
  
## 備註  
 C 和 C\+\+ 的每個實作都支援其主機電腦或作業系統獨有的一些功能。  例如，有些程式必須精確掌控放置資料的記憶體區域，或是控制某些函式接收參數的方式。  `#pragma` 指示詞提供了一種方式，讓每個編譯器能夠提供電腦和作業系統專屬功能，同時還能保留與 C 及 C\+\+ 語言的整體相容性。  
  
 Pragma 依定義為電腦或作業系統所專用，對每個編譯器而言通常各不相同。  Pragma 可用於條件陳述式、提供新的前置處理器功能，或是提供實作定義資訊給編譯器。  
  
 `token-string` 是一連串提供特定編譯器指令及引數 \(如果有的話\) 的字元。  數字符號 \(**\#**\) 必須是包含 pragma 的程式行上的第一個非空白字元，空白字元可能會分隔數字符號和 "pragma" 這個字。  在 `#pragma` 之後，撰寫轉譯工具可以剖析為前置處理語彙基元的任何文字。  `#pragma` 的引數會受巨集展開的限制。  
  
 如果編譯器發現無法辨識的 pragma，它會發出警告並繼續編譯。  
  
 Microsoft C 和 C\+\+ 編譯器可辨識下列 pragma：  
  
||||  
|-|-|-|  
|[alloc\_text](../preprocessor/alloc-text.md)|[auto\_inline](../preprocessor/auto-inline.md)|[bss\_seg](../preprocessor/bss-seg.md)|  
|[check\_stack](../preprocessor/check-stack.md)|[code\_seg](../preprocessor/code-seg.md)|[comment](../preprocessor/comment-c-cpp.md)|  
|[component](../preprocessor/component.md)|[conform](../preprocessor/conform.md) <sup>1</sup>|[const\_seg](../preprocessor/const-seg.md)|  
|[data\_seg](../preprocessor/data-seg.md)|[deprecated](../preprocessor/deprecated-c-cpp.md)|[detect\_mismatch](../preprocessor/detect-mismatch.md)|  
|[fenv\_access](../preprocessor/fenv-access.md)|[float\_control](../preprocessor/float-control.md)|[fp\_contract](../preprocessor/fp-contract.md)|  
|[function](../preprocessor/function-c-cpp.md)|[hdrstop](../preprocessor/hdrstop.md)|[include\_alias](../preprocessor/include-alias.md)|  
|[init\_seg](../preprocessor/init-seg.md) <sup>1</sup>|[inline\_depth](../preprocessor/inline-depth.md)|[inline\_recursion](../preprocessor/inline-recursion.md)|  
|[intrinsic](../preprocessor/intrinsic.md)|[loop](../preprocessor/loop.md) <sup>1</sup>|[make\_public](../preprocessor/make-public.md)|  
|[managed](../preprocessor/managed-unmanaged.md)|[message](../preprocessor/message.md)||  
|[omp](../preprocessor/omp.md)|[once](../preprocessor/once.md)||  
|[optimize](../preprocessor/optimize.md)|[pack](../preprocessor/pack.md)|[pointers\_to\_members](../preprocessor/pointers-to-members.md) <sup>1</sup>|  
|[pop\_macro](../preprocessor/pop-macro.md)|[push\_macro](../preprocessor/push-macro.md)|[region、endregion](../preprocessor/region-endregion.md)|  
|[runtime\_checks](../preprocessor/runtime-checks.md)|[section](../preprocessor/section.md)|[setlocale](../preprocessor/setlocale.md)|  
|[strict\_gs\_check](../preprocessor/strict-gs-check.md)|[unmanaged](../preprocessor/managed-unmanaged.md)|[vtordisp](../preprocessor/vtordisp.md) <sup>1</sup>|  
|[warning](../preprocessor/warning.md)|||  
  
 1.  只有 C\+\+ 編譯器支援。  
  
## Pragma 和編譯器選項  
 有些 pragma 提供與編譯器選項相同的功能。  當 pragma 在原始程式碼中出現時，它會覆寫編譯器選項指定的行為。  例如，如果您指定了 [\/Zp8](../build/reference/zp-struct-member-alignment.md)，您可以使用 [pack](../preprocessor/pack.md) 覆寫程式碼中特定區段的這個編譯器設定：  
  
```  
cl /Zp8 ...  
  
<file> - packing is 8  
// ...  
#pragma pack(push, 1) - packing is now 1  
// ...  
#pragma pack(pop) - packing is 8  
</file>  
```  
  
## \_\_pragma\(\) 關鍵字  
 **Microsoft 專有的**  
  
 編譯器也支援 `__pragma` 關鍵字，其功能與 `#pragma` 指示詞相同，但是可以在巨集定義中以內嵌方式使用。  `#pragma` 指示詞無法在巨集定義中使用，因為編譯器會將指示詞中的數字符號字元 \('\#'\) 解譯為[字串化運算子 \(\#\)](../preprocessor/stringizing-operator-hash.md)。  
  
 下列程式碼範例將示範如何在巨集中使用 `__pragma` 關鍵字。  這段程式碼摘錄自＜編譯器 COM 支援範例＞中 ACDUAL 範本的 mfcdual.h 標頭：  
  
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
  
 **結束 Microsoft 專有**  
  
## 請參閱  
 [C\/C\+\+ 前置處理器參考](../preprocessor/c-cpp-preprocessor-reference.md)   
 [C Pragma](../c-language/c-pragmas.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)