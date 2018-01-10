---
title: "延遲載入 Helper 函式，Visual c + + 6.0 之後 DLL 中的變更 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- delayed loading of DLLs, what's changed
- PFromRva method
- __delayLoadHelper2 function
- helper functions, what's changed
ms.assetid: 99f0be69-105d-49ba-8dd5-3be7939c0c72
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b3123a722e0e95119a4b04f5c060bd947b987cdf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="changes-in-the-dll-delayed-loading-helper-function-since-visual-c-60"></a>Visual C++ 6.0 之後 DLL 延遲載入 Helper 函式的變更
如果您電腦上有多個版本的 Visual c + +，或如果您定義自己的 helper 函式，您可能會受到變更 DLL 延遲載入 helper 函式。 例如:   
  
-   **__delayLoadHelper**現在**__delayLoadHelper2**  
  
-   **__pfnDliNotifyHook**現在**__pfnDliNotifyHook2**  
  
-   **__pfnDliFailureHook**現在**__pfnDliFailureHook2**  
  
-   **__FUnloadDelayLoadedDLL**現在**__FUnloadDelayLoadedDLL2**  
  
> [!NOTE]
>  如果您使用預設的 helper 函式，這些變更不會影響您。 沒有任何變更，叫用連結器的方式。  
  
## <a name="multiple-versions-of-visual-c"></a>多個版本的 Visual c + +  
 如果您的電腦上有多個版本的 Visual c + +，請確定連結器符合 delayimp.lib。 如果不相符，就會報告 連結器錯誤`___delayLoadHelper2@8`或`___delayLoadHelper@8`為無法解析的外部符號。 前者表示新的連結器，使用舊的 delayimp.lib，後者表示舊與新 delayimp.lib 連結器。  
  
 如果您收到無法解析的連結器錯誤，請執行[dumpbin /linkermember](../../build/reference/linkermember.md)： 在您要包含 helper 函式，以便查看哪些協助程式函式會改為定義 delayimp.lib 1。 Helper 函式也可以定義在目的檔;執行[dumpbin /symbols](../../build/reference/symbols.md)並尋找`delayLoadHelper(2)`。  
  
 如果您知道您有 Visual c + + 6.0 連結器，然後：  
  
-   延遲載入 helper.lib 或.obj 檔案，以判斷它是否定義上執行 dumpbin **__delayLoadHelper2**。 如果沒有，連結將會失敗。  
  
-   定義**__delayLoadHelper**延遲載入 helper 的.lib 或.obj 檔案。  
  
## <a name="user-defined-helper-function"></a>使用者定義的 Helper 函式  
 如果您定義自己的 helper 函式，並使用目前版本的 Visual c + +，執行下列作業：  
  
-   重新命名的 helper 函式**__delayLoadHelper2**。  
  
-   由於延遲描述項 (ImgDelayDescr 中 delayimp.h) 中的指標已經從絕對位址 (VAs) 變更為相對位址 (Rva)，如預期般在兩個 32 和 64 位元程式運作，您必須將這些回轉換成指標。 已導入了新的函式： PFromRva，delayhlp.cpp 中找到。 您可以在每個描述元中的欄位上使用此函式將它們轉換回 32 或 64 位元指標。 預設的延遲載入 helper 函式仍然是很好的範本，以做為範例。  
  
## <a name="load-all-imports-for-a-delay-loaded-dll"></a>載入延遲載入 DLL 的所有匯入  
 連結器可以從您指定要延遲載入 DLL 載入所有匯入。 請參閱[載入延遲載入 dll 的所有匯入](../../build/reference/loading-all-imports-for-a-delay-loaded-dll.md)如需詳細資訊。  
  
## <a name="see-also"></a>請參閱  
 [了解協助協助程式函式](understanding-the-helper-function.md)