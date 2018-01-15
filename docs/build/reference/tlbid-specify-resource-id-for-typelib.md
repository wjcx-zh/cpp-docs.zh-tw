---
title: "-TLBID （指定 TypeLib 的資源識別碼） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /tlbid
- VC.Project.VCLinkerTool.TypeLibraryResourceID
dev_langs: C++
helpviewer_keywords:
- tlb files, specifying resource ID
- -TLBID linker option
- .tlb files, specifying resource ID
- /TLBID linker option
- TLBID linker option
- type libraries, specifying resource ID
ms.assetid: 434b28a2-4656-4d52-ac82-8b18bf486fb2
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a552edab9f2de646de3b869bf84467924b5db348
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="tlbid-specify-resource-id-for-typelib"></a>/TLBID (指定 TypeLib 的資源 ID)
```  
/TLBID:id  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 `id`  
 連結器建立的類型程式庫的使用者指定的值。 它會覆寫預設資源識別碼為 1。  
  
## <a name="remarks"></a>備註  
 當編譯使用屬性的程式時，連結器會建立類型程式庫。 連結器將會指派至類型程式庫的資源識別碼為 1。  
  
 如果此資源 ID 與您現有的資源的其中一個衝突，您可以使用 /TLBID 指定其他識別碼。 您可以傳遞給的值範圍`id`是 1 到 65535 之間。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下**內嵌 IDL**屬性頁。  
  
4.  修改**TypeLib 資源 ID**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryResourceID%2A>。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)