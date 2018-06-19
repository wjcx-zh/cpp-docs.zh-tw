---
title: 嚴重錯誤 C1128 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1128
dev_langs:
- C++
helpviewer_keywords:
- C1128
ms.assetid: 6f9580fd-ecef-48be-9780-dcf666704279
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1d2604b17b656efab3a3575469eff6a02df960c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33226261"
---
# <a name="fatal-error-c1128"></a>嚴重錯誤 C1128
區段數目超過目的檔格式的限制： 請以 /bigobj 編譯  
  
 .Obj 檔案超過允許的區段，COFF 物件檔案格式限制的數目。  
  
 此區段限制可能是使用結果[/Gy](../../build/reference/gy-enable-function-level-linking.md)和偵錯組建。**/Gy**導致移入其本身的 COMDAT 區段函式。 在偵錯組建中，沒有每個 COMDAT 函式的偵錯資訊區段。  
  
 有太多的內嵌函式時，也會造成 C1128。  
  
 若要更正這個錯誤，分成多個原始程式碼檔中的原始程式檔、 編譯而不需要 **/Gy**，或使用編譯[/bigobj （增加中的區段數目。Obj 檔）](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md)。  如果您不會編譯與 **/Gy**，您必須指定個別的最佳化因為 **/O2**和 **/O1**都隱含 **/Gy**。  
  
 可能的話，請編譯但不偵錯資訊。  
  
 您可能也需要在不同的來源檔案中，有特定的具現化的範本，而不是讓編譯器發出。  
  
 移植程式碼，C1128 可能是最先出現時使用 x64 編譯器及大部分更新版本與 x86 編譯器。 會有與每個編譯的函式相關聯的至少 4 個區段，x64 **/Gy**或從範本或類別內嵌內嵌： 程式碼，pdata，並偵錯資訊，可能是 xdata。  X86 不會有 pdata。