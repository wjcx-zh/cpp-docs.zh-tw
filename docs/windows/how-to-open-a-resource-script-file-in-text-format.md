---
title: 如何： 以文字格式開啟資源指令碼檔案 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.resource
dev_langs:
- C++
helpviewer_keywords:
- resource script files, opening in text format
- .rc files, opening in text format
- rc files, opening in text format
ms.assetid: 0bc57527-f53b-40c9-99a9-4dcbc5c9af57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 170d688988576d3cbc9c454eb84603f9660120a8
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2018
ms.locfileid: "39571216"
---
# <a name="how-to-open-a-resource-script-file-in-text-format"></a>如何：以文字格式開啟資源指令碼檔
有時候您會想要檢視專案資源指令碼 (.rc) 檔內容，而不想開啟其特定資源編輯器內的資源 (例如對話方塊)。 例如，您可能想要在資源檔中跨所有對話方塊搜尋字串，而不想個別開啟每個對話方塊。  
  
> [!NOTE]
>  如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
 您可以輕鬆檢視它所包含的所有資源，並執行所支援的全域作業的文字格式開啟資源檔[文字編輯器](http://msdn.microsoft.com/508e1f18-99d5-48ad-b5ad-d011b21c6ab1)。  
  
> [!NOTE]
>  資源編輯器不會直接讀取.rc 或 resource.h 檔。 資源編譯器會將它們編譯成 .aps 檔，以供資源編輯器使用。 此檔案是一個編譯步驟，只會儲存符號資料。 如同正常的編譯程序一般，編譯程序期間會捨棄非符號的資訊 (例如註解)。 每當 .aps 檔未與 .rc 檔同步時，就會重新產生 .rc 檔 (例如，當您儲存時，資源編輯器會覆寫 .rc 檔和 resource.h 檔)。 資源本身的任何變更都會繼續合併在 .rc 檔中，但當 .rc 檔被覆寫後，註解就會永遠遺失。 如需如何保留註解的資訊，請參閱[在編譯時期包含資源](../windows/how-to-include-resources-at-compile-time.md)。  
  
### <a name="to-open-a-resource-script-file-as-text"></a>將資源指令碼檔開啟為文字  
  
1.  從**檔案**功能表中選擇 **開放**，然後按一下 **檔案。**  
  
2.  在 **開啟檔案**對話方塊方塊中，瀏覽至您想要以文字格式檢視資源指令碼檔。  
  
3.  反白顯示檔案，然後按一下下拉箭號**開啟**按鈕 （位於按鈕右邊）。  
  
4.  選擇**開啟**從下拉式選單。  
  
5.  在 [**開啟**] 對話方塊中，按一下**原始程式碼 （文字） 編輯器**。  
  
6.  從**開啟為**下拉式清單中，選取**文字**。  
  
     資源隨即在 [原始程式碼編輯器] 中開啟。  
  
 \-或-  
  
1.  在 [**方案總管] 中**，以滑鼠右鍵按一下.rc 檔。  
  
2.  從捷徑功能表，選擇 **開啟方式...**，然後選取**原始程式碼 （文字） 編輯器**。  
  
## <a name="requirements"></a>需求  
  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [資源檔](../windows/resource-files-visual-studio.md)   
 [資源編輯器](../windows/resource-editors.md)