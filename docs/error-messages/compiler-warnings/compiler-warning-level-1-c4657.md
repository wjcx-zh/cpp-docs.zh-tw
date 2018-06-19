---
title: 編譯器警告 （層級 1） C4657 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4657
dev_langs:
- C++
helpviewer_keywords:
- C4657
ms.assetid: eb750050-cea6-4ead-b80c-d5dcd4971cfc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 270cfb458b43d72ca1102cee128ed5998d74f665
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284361"
---
# <a name="compiler-warning-level-1-c4657"></a>編譯器警告 (層級 1) C4657
運算式包含自最新組建之後才新增的資料類型  
  
 您已加入或變更資料類型，使它成為對您的原始程式碼而言是上次成功組建之後所新增。 [編輯後繼續] 不支援對現有資料類型的變更。  
  
 這個警告後面一律會接著 [嚴重錯誤 C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md)。 如需詳細資訊，請參閱 [支援的程式碼變更](/visualstudio/debugger/supported-code-changes-cpp)。  
  
### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>移除這個警告，而不結束目前的偵錯工作階段  
  
1.  請將資料類型改回錯誤之前的狀態。  
  
2.  從 [偵錯]  功能表選擇 [套用程式碼變更] 。  
  
### <a name="to-remove-this-error-without-changing-your-source-code"></a>移除這個錯誤，而不變更您的原始程式碼  
  
1.  從 [偵錯]  功能表選擇 [停止偵錯] 。  
  
2.  從 [建置]  功能表選擇 [建置] 。