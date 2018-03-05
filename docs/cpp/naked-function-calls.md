---
title: "Naked 函式呼叫 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- virtual device drivers
- VXD virtual device drivers
- virtual device drivers, naked function calls
- naked functions
- prolog code
- epilog code
- naked keyword [C++]
- naked keyword [C++], storage-class attribute
ms.assetid: 2a66847a-a43f-4541-a7be-c9f5f29b5fdb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eed53718d211ac2152978c2a4d36e6a82c5c8024
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="naked-function-calls"></a>Naked 函式呼叫
## <a name="microsoft-specific"></a>Microsoft 特定的  
 函式宣告與`naked`屬性發出時不會包含初構和終解程式碼，讓您撰寫您自己使用的自訂初構/終解序列[內嵌組譯工具](../assembler/inline/inline-assembler.md)。 Naked 函式是做為進階功能提供。 這些函式可讓您宣告從 C/C++ 以外的內容呼叫的函式，因此對於參數位置以及要保留哪些暫存器會做出不同的假設。 範例包括像是中斷處理常式這類常式。 這項功能對於虛擬裝置驅動程式 (VxD) 的撰寫者特別實用。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [naked](../cpp/naked-cpp.md)  
  
-   [Naked 函式的規則和限制](../cpp/rules-and-limitations-for-naked-functions.md)  
  
-   [撰寫初構/終解程式碼的考量](../cpp/considerations-for-writing-prolog-epilog-code.md)  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [呼叫慣例](../cpp/calling-conventions.md)