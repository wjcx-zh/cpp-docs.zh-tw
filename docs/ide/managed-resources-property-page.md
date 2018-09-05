---
title: 受控資源屬性頁 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCManagedResourceCompilerTool.ResourceFileName
- VC.Project.VCManagedResourceCompilerTool.OutputFileName
- VC.Project.VCManagedResourceCompilerTool.DefaultLocalizedResources
dev_langs:
- C++
helpviewer_keywords:
- Managed Resources property page
ms.assetid: 80b80384-ee55-494d-9f0e-907bb98cfc19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e88f7ccf6f510ad5bcc7178af87714ca22a97252
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43688607"
---
# <a name="managed-resources-property-page"></a>Managed 資源屬性頁
啟用資源編譯器的設定。  
  
 [受控資源] 屬性頁包含下列屬性：  
  
 **資源邏輯名稱**  
 指定所產生之中繼 .resources 檔案的「邏輯名稱」。 邏輯名稱是用來載入資源的名稱。 如果未指定任何邏輯名稱，則會使用資源檔 (.resx) 名稱作為邏輯名稱。  
  
 **輸出檔名稱**  
 指定資源檔 (.resx) 所提供的最後輸出檔的名稱。  
  
 **預設的當地語系化資源**  
 指定給定的 .resx 檔案是提供預設的資源或附屬 .dll。  
  
 如需如何存取 [受控資源] 屬性頁的詳細資訊，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。  
  
## <a name="see-also"></a>請參閱  
 [使用 RC (RC 命令列)](/windows/desktop/menurc/using-rc-the-rc-command-line-)   
 [屬性頁](../ide/property-pages-visual-cpp.md)   
 [/ASSEMBLYRESOURCE (內嵌 Managed 資源)](../build/reference/assemblyresource-embed-a-managed-resource.md)