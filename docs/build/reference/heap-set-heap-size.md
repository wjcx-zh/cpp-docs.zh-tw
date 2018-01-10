---
title: "-HEAP （設定堆積大小） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.HeapCommitSize
- /heap
- VC.Project.VCLinkerTool.HeapReserveSize
dev_langs: C++
helpviewer_keywords:
- -HEAP linker option
- heap allocation, setting heap size
- /HEAP linker option
- HEAP linker option
ms.assetid: a3f71927-7f1d-492c-9fdb-dfccb1a043da
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1ddbbeb373a5c1c9a7b5a14d124900782048fbeb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="heap-set-heap-size"></a>/HEAP (設定堆積大小)
```  
/HEAP:reserve[,commit]  
```  
  
## <a name="remarks"></a>備註  
 /HEAP 選項會設定堆積的大小，以位元組為單位。 此選項時，只用於建置的.exe 檔案。  
  
 *保留*引數指定虛擬記憶體中堆積配置的總計。 預設的堆積大小為 1 MB。 連結器會無條件進位到最接近的 4 個位元組指定的值。  
  
 選擇性`commit`引數受限於作業系統所解譯。 在 NT/Windows 2000 中，它會指定一次配置的實體記憶體數量。 已認可的虛擬記憶體會造成要保留在分頁檔的空間。 較高`commit`值可以節省的時間，當應用程式需要較多的堆積空間，但會增加記憶體需求且可能的啟動時間。  
  
 指定*保留*和`commit`decimal 或 C 語言標記法中的值。  
  
 這項功能也會提供模組定義檔與透過[HEAPSIZE](../../build/reference/heapsize.md)。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下**系統**屬性頁。  
  
4.  修改**堆積基本配置大小**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapReserveSize%2A>和<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapCommitSize%2A>。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)