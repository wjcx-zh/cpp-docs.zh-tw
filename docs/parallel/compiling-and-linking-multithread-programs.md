---
title: 編譯和連結多執行緒程式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- compiling multithreaded programs
- multithreading [C++], linking programs
- threading [C++], linking programs
- multithreading [C++], compiled programs
- threading [C++], compiled programs
- compiling source code [C++], multithread programs
- linking [C++], multithread programs
ms.assetid: 27589afc-daf2-4f26-b868-a99de5c9dfec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ab667e372c8118a83b7a93444abbfbc5c19b6e0
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131514"
---
# <a name="compiling-and-linking-multithread-programs"></a>編譯和連結多執行緒程式
Bounce.c 程式在引進[多執行緒 C 程式範例](sample-multithread-c-program.md)。  
  
程式會編譯多執行緒的預設值。  
  
### <a name="to-compile-and-link-the-multithread-program-bouncec-from-within-the-development-environment"></a>若要編譯和連結多執行緒程式 Bounce.c 從開發環境  
  
1.  按一下 [ **檔案** ] 功能表上的 [ **新增**]，然後按一下 [ **專案**]。  
  
2.  在 **專案類型**窗格中，按一下**Win32**。  
  
3.  在 **範本**窗格中，按一下**Win32 主控台應用程式**，然後再將專案命名。  
  
4.  加入包含 C 原始程式碼檔案加入專案。  
  
5.  在 **建置**功能表上，建置專案，依序按一下**建置**命令。  
  
### <a name="to-compile-and-link-the-multithread-program-bouncec-from-the-command-line"></a>若要編譯和連結多執行緒程式 Bounce.c，從命令列  
  
1.  編譯和連結的程式：  
  
    ```  
    CL BOUNCE.C  
    ```  
  
## <a name="see-also"></a>另請參閱

[使用 C 和 Win32 進行多執行緒處理](multithreading-with-c-and-win32.md)