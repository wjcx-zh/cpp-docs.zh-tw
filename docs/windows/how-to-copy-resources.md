---
title: 如何： 複製資源 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.resvw.resource.copying
- vs.resvw.resource.copying
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], moving between files
- resources [Visual Studio], copying
- resource files, copying or moving resources between
- resource files, tiling
- .rc files, copying resources between
- rc files, copying resources between
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eb93f90b6d96d679b055893dc13adaa0d3c2e780
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642977"
---
# <a name="how-to-copy-resources"></a>如何：複製資源
您可以從一個檔案複製的資源，到另一個，而不需要變更它們，或者您也可以[變更其語言或條件的資源，同時將它複製](../windows/how-to-change-the-language-or-condition-of-a-resource-while-copying.md)。  
  
 您可以輕鬆地將複製資源從現有的資源或可執行檔目前的資源檔。 若要這樣做，您開啟包含資源，同時這兩個檔案並將項目從一個檔案拖曳到另一個或複製並貼兩個檔案之間。 這個方法適用於資源指令碼 (.rc) 檔和資源範本 (.rct) 檔，以及可執行檔 (.exe) 檔案。  
  
> [!NOTE]
>  Visual c + + 包含您可以使用自己的應用程式中的範例資源檔案。 如需詳細資訊，請參閱 <<c0> [ 美工圖案： 通用資源](http://msdn.microsoft.com/9bac2891-b6b3-49ec-a287-cec850c707e0)。  
  
 您可以使用拖放方法開啟.rc 檔之間[在專案外部](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。  
  
### <a name="to-copy-resources-between-files-using-the-drag-and-drop-method"></a>若要使用拖放方法的檔案間複製資源  
  
1.  開啟這兩個獨立的資源檔案 (如需詳細資訊，請參閱 < [.rc 檔案外部的專案中的 檢視資源](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md))。 例如，開啟 Source1.rc 和 Source2.rc。  
  
2.  在第一個.rc 檔中，按一下您想要複製的資源。 例如，在`Source1.rc`，按一下**IDD_DIALOG1**。  
  
3.  按住 CTRL 鍵並拖曳至第二個.rc 檔的資源。 例如，拖曳**IDD_DIALOG1**從`Source1.rc`至`Source2.rc`。  
  
    > [!NOTE]
    >  拖曳資源，不需按著**Ctrl**鍵會移動資源，而不是複製它。  
  
### <a name="to-copy-resources-using-copy-and-paste"></a>複製資源使用複製和貼上  
  
1.  開啟這兩個獨立的資源檔案 (如需詳細資訊，請參閱 < [.rc 檔案外部的專案中的 檢視資源](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md))。 比方說，Source1.rc 和 Source2.rc。  
  
2.  原始程式檔要複製的資源 (例如`Source1.rc`)，以滑鼠右鍵按一下資源，然後選擇 **複製**從捷徑功能表。  
  
3.  以滑鼠右鍵按一下您想要貼上資源所在的資源檔 (例如`Source2.rc`)。 選擇**貼上**從捷徑功能表。  
  
    > [!NOTE]
    >  您無法拖放、 複製、 剪下，或在專案中的資源檔案之間貼上 (**資源檢視**) 和獨立的.rc 檔的檔案 （在文件視窗中開啟）。 您可以在舊版的產品來這麼做。  
  
    > [!NOTE]
    >  若要避免衝突的符號名稱或現有的檔案中的值，Visual c + + 可能會變更已傳送的資源的符號值或符號名稱和值時將它複製到新的檔案。  
  
 如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [如何：在專案外開啟資源指令碼檔 (獨立式)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)  
 [資源檔](../windows/resource-files-visual-studio.md)   
 [資源編輯器](../windows/resource-editors.md)