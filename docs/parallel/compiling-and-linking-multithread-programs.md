---
title: "編譯和連結多執行緒程式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- compiling multithreaded programs
- multithreading [C++], linking programs
- threading [C++], linking programs
- multithreading [C++], compiled programs
- threading [C++], compiled programs
- compiling source code [C++], multithread programs
- linking [C++], multithread programs
ms.assetid: 27589afc-daf2-4f26-b868-a99de5c9dfec
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cdfae45dabc989113ec7305feed27ea6d697e422
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiling-and-linking-multithread-programs"></a>編譯和連結多執行緒程式
中導入 Bounce.c 程式[多執行緒 C 程式範例](../parallel/sample-multithread-c-program.md)。  
  
 編譯程式會根據預設，多執行緒。  
  
#### <a name="to-compile-and-link-the-multithread-program-bouncec-from-within-the-development-environment"></a>若要編譯及連結多執行緒程式 Bounce.c 從開發環境中  
  
1.  按一下 [ **檔案** ] 功能表上的 [ **新增**]，然後按一下 [ **專案**]。  
  
2.  在**專案類型**] 窗格中，按一下 [ **Win32**。  
  
3.  在**範本**] 窗格中，按一下 [ **Win32 主控台應用程式**，，然後將專案。  
  
4.  加入包含 C 原始程式碼檔案加入專案。  
  
5.  在**建置**功能表上，建置專案，依序按一下**建置**命令。  
  
#### <a name="to-compile-and-link-the-multithread-program-bouncec-from-the-command-line"></a>若要編譯及連結多執行緒程式 Bounce.c 從命令列  
  
1.  編譯及連結程式：  
  
    ```  
    CL BOUNCE.C  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [使用 C 和 Win32 進行多執行緒處理](../parallel/multithreading-with-c-and-win32.md)