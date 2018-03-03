---
title: "受資源編輯影響的檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- resource editing
- resources [Visual Studio], editing
ms.assetid: d0820df1-ba84-40ac-bce9-29ea5ee7e3f8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3b3a5f8c8351d7056409b0e6182862213c51381a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="files-affected-by-resource-editing"></a>受資源編輯影響的檔案
Visual Studio 環境會在您的資源編輯工作階段期間使用下表中顯示的檔案。  
  
|檔案名稱|描述|  
|---------------|-----------------|  
|偵錯工具|開發環境所產生的標頭檔；包含符號定義。|  
|Filename.aps|目前資源指令碼檔的二進位版本；用於快速載入。<br /><br /> 資源編輯器不會直接讀取.rc 或 resource.h 檔。 資源編譯器會將它們編譯成 .aps 檔，以供資源編輯器使用。 此檔案是一個編譯步驟，只會儲存符號資料。 如同正常的編譯程序一般，編譯程序期間會捨棄非符號的資訊 (例如註解)。 每當 .aps 檔未與 .rc 檔同步時，就會重新產生 .rc 檔 (例如，當您儲存時，資源編輯器會覆寫 .rc 檔和 resource.h 檔)。 資源本身的任何變更都會繼續合併在 .rc 檔中，但當 .rc 檔被覆寫後，註解就會永遠遺失。 在註解保留方式的資訊，請參閱[在編譯時期包含資源](../windows/how-to-include-resources-at-compile-time.md)。|  
|.rc|包含目前專案中的資源所適用之指令碼的資源指令碼檔。 .aps 檔會在您每次存檔時覆寫此檔案。|  
  

  
## <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>請參閱  
 [資源檔](../windows/resource-files-visual-studio.md)