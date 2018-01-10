---
title: "載入延遲載入 DLL 的所有匯入 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: __HrLoadAllImportsForDll linker option
ms.assetid: 975fcd97-1a56-4a16-9698-e1a249d2d592
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8afa206e62702407d9974802f9422c8597d772ce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="loading-all-imports-for-a-delay-loaded-dll"></a>載入延遲載入 DLL 的所有匯入
**__HrLoadAllImportsForDll**函式，以定義在 delayhlp.cpp，指示連結器從所指定的 DLL 載入所有匯入[/delayload](../../build/reference/delayload-delay-load-import.md)連結器選項。  
  
 載入所有匯入可讓您使程式碼中的一個位置中的錯誤處理，並不需要使用例外狀況處理的匯入實際的呼叫周圍。 它也可避免透過程序因為無法載入匯入的協助程式程式碼部分失敗應用程式的情況。  
  
 呼叫**__HrLoadAllImportsForDll**不會變更行為的攔截程序和錯誤處理，請參閱[錯誤處理和通知](../../build/reference/error-handling-and-notification.md)如需詳細資訊。  
  
 DLL 名稱傳遞給**__HrLoadAllImportsForDll**會比較儲存在 DLL 本身的名稱，並會區分大小寫。  
  
 下列範例示範如何呼叫**__HrLoadAllImportsForDll**:  
  
```  
if (FAILED(__HrLoadAllImportsForDll("delay1.dll"))) {  
   printf ( "failed on snap load, exiting\n" );  
   exit(2);  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [延遲載入 DLL 的連結器支援](../../build/reference/linker-support-for-delay-loaded-dlls.md)