---
title: 例外狀況處理 （c + + 元件擴充功能） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- structured exception handling, managed exceptions
- Exception class, managed applications
- exception handling
- C++ exception handling
- exception handling, types of
- managed exceptions
- System::Exception class in managed applications
ms.assetid: ccb11fe8-6938-41ac-b477-a183e85865b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6b6dcf8e844fbb2e8e133dc5dc6f0b98a3166ac6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877731"
---
# <a name="exception-handling--c-component-extensions"></a>例外狀況處理 (C++ 元件擴充功能)
使用應用程式編譯 **/ZW**編譯器選項或 **/clr**編譯器選項都使用*例外狀況*處理程式執行期間發生意外的錯誤。 下列主題將討論 C++/CX 或 C++/CLI 應用程式中的例外狀況處理。  
  
## <a name="in-this-section"></a>本節內容  
 [使用 Managed 例外狀況的基本概念](../dotnet/basic-concepts-in-using-managed-exceptions.md)  
 描述擲回例外狀況，並使用`try` / `catch`區塊。  
  
 [例外狀況處理在 /CLR 下的行為差異](../dotnet/differences-in-exception-handling-behavior-under-clr.md)  
 討論與標準 C++ 例外狀況處理行為的差異。  
  
 [finally](../dotnet/finally.md)  
 討論如何使用 finally 關鍵字。  
  
 [如何：定義與安裝全域例外狀況處理常式](../dotnet/how-to-define-and-install-a-global-exception-handler.md)  
 示範如何擷取未處理的例外狀況。  
  
 [如何：攔截 MSIL 擲回之機器碼的例外狀況](../dotnet/how-to-catch-exceptions-in-native-code-thrown-from-msil.md)  
 討論如何攔截機器碼中的 CLR 和 C++ 例外狀況。  
  
 [如何：定義與安裝全域例外狀況處理常式](../dotnet/how-to-define-and-install-a-global-exception-handler.md)  
 示範如何攔截所有未處理的例外狀況。  
  
## <a name="related-sections"></a>相關章節  
 [例外狀況處理](../cpp/exception-handling-in-visual-cpp.md)  
 描述 C++ 中的例外狀況處理。  
  
## <a name="see-also"></a>另請參閱  
 [執行階段平台的元件延伸模組](../windows/component-extensions-for-runtime-platforms.md)