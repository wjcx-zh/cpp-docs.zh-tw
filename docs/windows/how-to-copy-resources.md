---
title: "如何： 複製資源 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.resvw.resource.copying
- vs.resvw.resource.copying
dev_langs: C++
helpviewer_keywords:
- resources [Visual Studio], moving between files
- resources [Visual Studio], copying
- resource files, copying or moving resources between
- resource files, tiling
- .rc files, copying resources between
- rc files, copying resources between
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4ac30e57c0c833f5d26cf9aa8a9ed4ba43946bb3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-copy-resources"></a>如何：複製資源
您可以從一個檔案複製資源，到另一個，而不需要變更它們，或者您可以[變更語言或條件的資源，同時將它複製](../windows/how-to-change-the-language-or-condition-of-a-resource-while-copying.md)。  
  
 您可以輕鬆地將複製資源從現有的資源或可執行檔目前的資源檔。 若要這樣做，請您開啟包含資源，同時這兩個檔案和一個檔案之間拖曳項目或複製並貼兩個檔案之間。 這個方法適用於資源指令碼 (.rc) 檔和資源範本 (.rct) 檔，以及可執行檔 (.exe) 檔案。  
  
> [!NOTE]
>  Visual c + + 包含您可以使用自己的應用程式中的範例資源檔案。 如需詳細資訊，請參閱[美工圖案： 通用資源](http://msdn.microsoft.com/en-us/9bac2891-b6b3-49ec-a287-cec850c707e0)。  
  
 您可以使用拖放方法開啟的.rc 檔之間[專案以外](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。  
  
### <a name="to-copy-resources-between-files-using-the-drag-and-drop-method"></a>若要使用拖放方法的檔案間複製資源  
  
1.  開啟這兩個獨立的資源檔案 (如需詳細資訊，請參閱[的.rc 檔以外的專案中的 檢視資源](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md))。 例如，開啟 Source1.rc 和 Source2.rc。  
  
2.  在第一個.rc 檔中，按一下您想要複製的資源。 例如，在 Source1.rc，按一下 IDD_DIALOG1。  
  
3.  按住 CTRL 鍵並拖曳至第二個.rc 檔的資源。 例如，拖曳 Source1.rc 至 Source2.rc IDD_DIALOG1。  
  
    > [!NOTE]
    >  拖曳資源沒有按住 CTRL 鍵移動資源，而不是複製它。  
  
### <a name="to-copy-resources-using-copy-and-paste"></a>複製資源使用複製和貼上  
  
1.  開啟這兩個獨立的資源檔案 (如需詳細資訊，請參閱[的.rc 檔以外的專案中的 檢視資源](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md))。 例如，Source1.rc 和 Source2.rc。  
  
2.  在來源檔案中您要複製資源 (例如，Source1.rc)，以滑鼠右鍵按一下資源，然後選擇 **複製**從捷徑功能表。  
  
3.  以滑鼠右鍵按一下您想要貼上的資源 (例如，Source2.rc) 所在的資源檔。 選擇**貼上**從捷徑功能表。  
  
    > [!NOTE]
    >  您無法拖放、 複製、 剪下、 或專案 （資源檢視） 中的資源檔和獨立的.rc 檔 （其在文件視窗中開啟） 之間貼上。 在舊版產品中，您無法執行這項操作。  
  
    > [!NOTE]
    >  若要避免衝突的符號名稱或現有的檔案中的值，Visual c + + 可能會變更傳送的資源的符號值或符號名稱和值時將它複製到新的檔案。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中*.NET Framework 開發人員手冊 》。* 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理應用程式的資源上的資訊，請參閱[全球化和當地語系化的.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
 需求  
  
 Win32  
  
## <a name="see-also"></a>請參閱  
 [如何： 開啟專案 （獨立） 外的資源指令碼檔案](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)   
 [資源檔](../windows/resource-files-visual-studio.md)   
 [資源編輯器](../windows/resource-editors.md)