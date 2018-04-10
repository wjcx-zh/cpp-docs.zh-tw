---
title: 動態連結至 MFC 的標準的 MFC DLL 的模組狀態 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- module states [C++]
- MFC DLLs [C++], regular MFC DLLs
- module states [C++], regular MFC DLLs dynamically linked to
- DLLs [C++], module states
ms.assetid: b4493e79-d25e-4b7f-a565-60de5b32c723
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8b88f895255c698f04b6988e63b8b75372fa59b0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="module-states-of-a-regular-mfc-dll-dynamically-linked-to-mfc"></a>動態連結至 MFC 的標準的 MFC DLL 的模組狀態
動態連結至 MFC DLL 的 一般 MFC DLL 的能力可讓非常複雜的某些設定。 比方說，標準的 MFC DLL 和其使用的可執行檔可以同時動態連結至 MFC DLL 以及任何 MFC 擴充 Dll。  
  
 這個組態會有問題，對於 MFC 全域資料，例如目前的指標`CWinApp`物件和控制代碼的對應。  
  
 MFC 4.0 版，這個全域資料常駐於 MFC DLL 本身前後程序中所有模組所共用。 因為使用 Win32 DLL 的每個處理程序會取得自己的 DLL 資料的複本，此配置會提供簡單的方法，來追蹤每個處理序的資料。 此外，因為 AFXDLL 模型假設，會有一個`CWinApp`物件和一組處理程序中的對應，MFC DLL 本身中可追蹤這些項目。  
  
 但能夠以動態方式將標準的 MFC DLL 連結至 MFC DLL，它現在可能有兩個或多個`CWinApp`處理程序中的物件，和也兩個或多個集合的處理常式對應。 如何沒有 MFC 追蹤的哪些應該使用？  
  
 解決方案是讓每個模組 （應用程式或 MFC 的標準 DLL） 本身的全域狀態資訊。 因此，呼叫**AfxGetApp**在一般 MFC DLL 將指標傳回至`CWinApp`DLL，而不是可執行檔中的物件。 MFC 的全域資料這每個模組份稱為模組狀態，而且述[MFC 技術提示 58](../mfc/tn058-mfc-module-state-implementation.md)。  
  
 一般 MFC 視窗程序會自動切換到正確的模組狀態，因此您不需要擔心，在標準的 MFC DLL 中實作的任何訊息處理常式。 但是，當可執行檔呼叫 MFC 的標準 DLL，您需要明確地將目前的模組狀態設定為 DLL。 若要這樣做，請使用**AFX_MANAGE_STATE**從 DLL 匯出的每個函式中的巨集。 這是從 DLL 匯出的函式的開頭加入下列程式碼行：  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))  
```  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [管理 MFC 模組的狀態資料](../mfc/managing-the-state-data-of-mfc-modules.md)  
  
-   [動態連結至 MFC 的標準 MFC Dll](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [MFC 延伸模組 DLL](../build/extension-dlls-overview.md)  
  
## <a name="see-also"></a>請參閱  
 [Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)