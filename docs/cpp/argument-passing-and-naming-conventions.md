---
title: 引數傳遞和命名慣例 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- argument passing [C++], conventions
- arguments [C++], widening
- coding conventions, arguments
- arguments [C++], passing
- registers, return values
- thiscall keyword [C++]
- naming conventions [C++], arguments
- arguments [C++], naming
- passing arguments [C++], conventions
- conventions [C++], argument names
ms.assetid: de468979-eab8-4158-90c5-c198932f93b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4e1a6a8e837a44a966f262f581db04f1589233c8
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404037"
---
# <a name="argument-passing-and-naming-conventions"></a>引數傳遞和命名慣例
**Microsoft 專屬**  
  
 Visual C++ 編譯器允許您指定在函式和呼叫端之間傳遞引數和傳回值的慣例。 並非所有慣例都適用於所有支援的平台，部分慣例會使用平台特定實作。 在大部分情況下，會忽略在特定平台上指定不支援慣例的關鍵字或編譯器參數，並且使用平台預設慣例。  
  
 在 x86 平台上傳遞引數時，會將所有引數擴大為 32 位元。 傳回值也會被擴大為 32 位元並在 EAX 暫存器中傳回，但 8 位元組結構例外，它是在 EDX:EAX 暫存器組中傳回。 較大的結構會在 EAX 暫存器中以隱藏傳回結構的指標傳回。 參數會從右至左推送至堆疊。 非 POD 的結構不會在暫存器中傳回。  
  
 如果在函式中使用 ESI、EDI、EBX 和 EBP 暫存器，編譯器會產生初構和終解程式碼來儲存和還原這些暫存器。  
  
> [!NOTE]
>  從函式以傳值方式傳回結構、等位或類別時，類型的所有定義必須相同，否則程式可能會在執行階段失敗。  
  
 如需如何定義您自己的函式初構和終解程式碼的資訊，請參閱[Naked 函式呼叫](../cpp/naked-function-calls.md)。  
  
 預設值的相關資訊，請在目標為 x64 平台，請參閱的程式碼中呼叫慣例[概觀的 x64 呼叫慣例](../build/overview-of-x64-calling-conventions.md)。 在 ARM 平台為目標的程式碼中呼叫慣例問題的詳細資訊，請參閱[Visual c + + ARM 移轉常見問題](../build/common-visual-cpp-arm-migration-issues.md)。  
  
 Visual C/C++ 編譯器支援下列呼叫慣例。  
  
|關鍵字|堆疊清除|參數傳遞|  
|-------------|-------------------|-----------------------|  
|[__cdecl](../cpp/cdecl.md)|呼叫端|以相反順序 (從右至左) 將參數推送至堆疊|  
|[__clrcall](../cpp/clrcall.md)|N/A|依照順序 (從左至右) 將參數載入至 CLR 運算式堆疊。|  
|[__stdcall](../cpp/stdcall.md)|被呼叫端|以相反順序 (從右至左) 將參數推送至堆疊|  
|[__fastcall](../cpp/fastcall.md)|被呼叫端|儲存在暫存器中，然後推送至堆疊|  
|[__thiscall](../cpp/thiscall.md)|被呼叫端|推送到堆疊;**這**指標儲存在 ECX 中|  
|[__vectorcall](../cpp/vectorcall.md)|被呼叫端|儲存在暫存器中，然後以相反順序 (從右至左) 推送至堆疊|  
  
 如需相關資訊，請參閱[過時呼叫慣例](../cpp/obsolete-calling-conventions.md)。  
  
 **結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [呼叫慣例](../cpp/calling-conventions.md)