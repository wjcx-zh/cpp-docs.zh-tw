---
title: "-APPCONTAINER （Windows 市集應用程式） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 9a432db5-7640-460b-ab18-6f61fa7daf6f
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 22ca7bec885f20518950626d33f7e3af553d0d52
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="appcontainer-windows-store-app"></a>/APPCONTAINER (Windows 市集應用程式)
指定連結器是否會建立可執行映像必須在應用程式容器中執行。  
  
## <a name="syntax"></a>語法  
  
```  
/APPCONTAINER[:NO]  
```  
  
## <a name="remarks"></a>備註  
 根據預設，/APPCONTAINER 為關閉。  
  
 這個選項修改可執行檔，以指出是否必須在 appcontainer 處理序隔離環境中執行應用程式。 /APPCONTAINER 指定必須在 appcontainer 環境中執行的應用程式 — 例如，[!INCLUDE[win8_appstore_long](../../build/reference/includes/win8_appstore_long_md.md)]應用程式。 (選項會自動設定 Visual Studio 中建立時[!INCLUDE[win8_appstore_long](../../build/reference/includes/win8_appstore_long_md.md)]從範本的應用程式。)桌面應用程式中，指定 /APPCONTAINER:NO 或只省略選項。  
  
 /APPCONTAINER 選項已引入[!INCLUDE[win8](../../build/reference/includes/win8_md.md)]。  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中設定這個連結器選項  
  
1.  開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  展開**組態屬性**節點。  
  
3.  展開**連結器**節點。  
  
4.  選取**命令列**屬性頁。  
  
5.  在**其他選項**，輸入`/APPCONTAINER`或`/APPCONTAINER:NO`。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)