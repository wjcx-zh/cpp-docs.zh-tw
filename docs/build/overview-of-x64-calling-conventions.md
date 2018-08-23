---
title: 概觀的 x64 呼叫慣例 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a05db5eb-0844-4d9d-8b92-b1b2434be0ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 850ab9f4d3656391ac744f42a9f7d4b962762724
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42573131"
---
# <a name="overview-of-x64-calling-conventions"></a>x64 呼叫慣例概觀
X86 和 x64 之間的兩個重要差異是 64 位元定址功能，以及一般的 16 個 64 位元暫存器設定一般用途。 提供擴充的暫存器組，使用 x64 [__fastcall](../cpp/fastcall.md)呼叫慣例和 risc 例外狀況處理模型。 `__fastcall`慣例會使用前四個引數的堆疊框架的暫存器傳遞其他引數。  
  
 下列編譯器選項可協助您最佳化您的應用程式 （x64):  
  
-   [/favor (專為架構最佳化)](../build/reference/favor-optimize-for-architecture-specifics.md)  
  
## <a name="calling-convention"></a>呼叫慣例  
 X64 應用程式二進位介面 (ABI) 會使用四個註冊快速呼叫的呼叫慣例的預設值。 呼叫堆疊上配置空間，作為被呼叫者來儲存這些暫存器的陰影存放區。 函式呼叫的引數和用於這些引數的暫存器之間沒有嚴格的一對一對應。 任何引數的不符合 8 個位元組，或不是 1、 2、 4 或 8 個位元組，必須傳址方式傳遞。 不會以單一引數分散到多個暫存器。 X87 暫存器堆疊是未使用。 它可能會由被呼叫端，但必須考慮 volatile 跨函式呼叫。 所有的浮點數作業會完成使用 16 XMM 暫存器。 整數引數會傳入暫存器 RCX、 RDX、 R8 和 R9。 浮點引數會傳入 XMM0L、 XMM1L、 XMM2L 和 XMM3L。 16 位元組引數是傳址方式傳遞。 在將詳細說明參數傳遞[參數傳遞](../build/parameter-passing.md)。 這些暫存器中，除了 RAX、 R10，R11，XMM4 和 XMM5 會視為 volatile。 所有其他暫存器是靜態。 暫存器使用方式中有詳細記載[註冊使用量](../build/register-usage.md)並[呼叫端/被呼叫端儲存註冊](../build/caller-callee-saved-registers.md)。  
  
 呼叫端會負責配置的空間被呼叫端，參數，而且即使被呼叫端不需要那麼多的參數，則一律必須配置足夠的空間來儲存四個的暫存器參數。 這可簡化沒有原型 C 語言函式和 vararg C/c + + 函式的支援。 Vararg 或 unprototyped 函式中，任何浮點值必須在對應一般用途的暫存器中重複。 前四個以外的任何參數都必須儲存在堆疊上，上述的第一的四個，在呼叫之前的陰影存放區中。 Vararg 函式詳細資料可在[Varargs](../build/varargs.md)。 沒有原型的函式資訊詳述[沒有原型的函式](../build/unprototyped-functions.md)。  
  
## <a name="alignment"></a>對齊  
 大部分的結構對齊至其自然對齊。 主要的例外狀況是堆疊指標並`malloc`或`alloca`專為 16 個位元組，以協助效能的記憶體。 16 個位元組以上的對齊必須手動完成，但由於 16 個位元組是常用的對齊方式大小 XMM 作業，這應可適用於大部分的程式碼。 如需結構的配置和對齊方式的詳細資訊請參閱 <<c0> [ 型別和儲存體](../build/types-and-storage.md)。 堆疊配置的相關資訊，請參閱[Stack 使用量](../build/stack-usage.md)。  
  
## <a name="unwindability"></a>Unwindability  
 分葉函式是函式不會變更任何非暫時性暫存器。 非分葉函式可能會變更非揮發性 RSP 比方說，呼叫函式，或為區域變數配置額外的堆疊空間。 若要處理的例外狀況時，請復原靜態暫存器，非分葉函式都必須以說明如何正確回溯任意指令處函式的靜態資料註解。 這項資料會儲存為*pdata*，或程序的資料，依序指向*xdata*、 例外狀況處理的資料。 Xdata 包含回溯的資訊，並可以指向其他 pdata 或例外狀況處理常式函式。 初構和終都具有高度限制，使它們可以適當地述 xdata。 堆疊指標必須對齊 16 個位元組，但不屬於初構的終解，在分葉函式內的程式碼的任何區域中。 分葉函式可以藉由模擬傳回，因此不需要 pdata 和 xdata 進行回溯。 如需函式初構和終適當的結構的詳細資訊，請參閱[初構和終解](../build/prolog-and-epilog.md)。 如需例外狀況處理和例外狀況處理和 pdata 和 xdata 回溯的詳細資訊，請參閱[例外狀況處理 (x64)](../build/exception-handling-x64.md)。  
  
## <a name="see-also"></a>另請參閱  
 [x64 軟體慣例](../build/x64-software-conventions.md)