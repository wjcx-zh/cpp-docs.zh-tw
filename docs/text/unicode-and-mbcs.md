---
title: Unicode 和 MBCS |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- _mbcs
dev_langs:
- C++
helpviewer_keywords:
- MBCS [C++], Unicode
- MFC [C++], character sets
- character sets [C++], multibyte
- run-time libraries [C++], language portability
- character sets [C++], Unicode
- Unicode [C++], MFC and C run-time functions
- multibyte characters [C++]
- runtime [C++], language portability
ms.assetid: 677baec6-71b4-4579-94df-64f18bc117c4
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2e10c07e11cbe940b5f7cfee460ddd33f6f5ff1f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857346"
---
# <a name="unicode-and-mbcs"></a>Unicode 和 MBCS
Microsoft Foundation Classes (MFC) 程式庫、 Visual c + +、 C 執行階段程式庫和 Visual c + + 開發環境會啟用可協助您的國際化程式設計。 它們提供：  
  
-   在 Windows 上的 Unicode 標準支援。 Unicode 是目前的標準，應該盡可能使用此標準。  
  
     Unicode 是 16 位元的字元編碼方式，提供足夠的編碼方式的所有語言。 所有的 ASCII 字元會包含在 Unicode，以擴大的字元。  
  
-   一種多位元組字元集 (MBCS) 支援所有平台上呼叫雙位元組字元集 (DBCS)。  
  
     DBCS 字元以 1 或 2 個位元組所組成。 某些範圍的位元組擱置一旁，使用做為前導位元組。 前導位元組會指定它和下列的後隨位元組組成單一的 2 位元組寬度字元。 您必須持續追蹤的哪些位元組是前導位元組。 在特定多位元組字元集中，前導位元組落在特定範圍內，後隨位元組也是如此。 當這些範圍重疊時，可能必須評估內容，以決定指定的位元組是前導位元組或後隨位元組。  
  
-   工具可簡化撰寫國際市場的應用程式的 MBCS 程式設計的支援。  
  
     Mbcs 的 Windows 作業系統版本，Visual c + + 開發系統上執行時，包括整合式原始檔的程式碼編輯器、 偵錯工具，以及命令列工具，已完全啟用 MBCS。 如需詳細資訊，請參閱[Visual c + + 中的 MBCS 支援](../text/mbcs-support-in-visual-cpp.md)。  
  
> [!NOTE]
>  在這份文件，MBCS 用來描述多位元組字元的所有非 Unicode 支援。 在 Visual c + +，MBCS 一律表示 DBCS。 字元集數目比不支援 2 個位元組寬。  
  
 根據定義，ASCII 字元集是所有多位元組字元集的子集。 在許多多位元組字元集中，0x00 - 0x7F 範圍中的每個字元都會與 ASCII 字元集中具有相同值的字元相同。 例如，ASCII 和 MBCS 字元字串中，1 位元組**NULL**字元 ('\0') 的值 0x00 處截斷，而且表示結束 null 字元。  
  
## <a name="see-also"></a>另請參閱  
 [文字和字串](../text/text-and-strings-in-visual-cpp.md)   
 [啟用國際化](../text/international-enabling.md)