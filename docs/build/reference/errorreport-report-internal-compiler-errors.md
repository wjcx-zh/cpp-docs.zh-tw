---
title: "-errorReport （回報編譯器內部錯誤） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.ErrorReporting
- /errorreport
dev_langs:
- C++
helpviewer_keywords:
- /errorReport compiler option [C++]
- -errorReport compiler option [C++]
ms.assetid: 819828f8-b0a5-412c-9c57-bf822f17e667
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9b34df09ca53441789fc90061748ad591149d6b2
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="errorreport-report-internal-compiler-errors"></a>/errorReport (回報編譯器內部錯誤)
讓您可將內部編譯器錯誤 (ICE) 資訊直接提供給 Microsoft。  
  
## <a name="syntax"></a>語法  
  
```  
/errorReport:[ none | prompt | queue | send ]  
```  
  
## <a name="arguments"></a>引數  
 **none**  
 將不會收集有關內部編譯器錯誤的報告，也不會將報告傳送給 Microsoft。  
  
 **提示**  
 提示您在收到內部編譯器錯誤時傳送報告。 **提示**是在開發環境中編譯應用程式時的預設值。  
  
 **queue**  
 佇列錯誤報告。 當您登入系統管理員權限時，會顯示視窗，以便您可以將任何失敗報告自上次登入 （不會提示您要傳送報告的失敗一次以上每隔三天）。 **佇列**應用程式會在命令提示字元進行編譯時是預設值。  
  
 **傳送**  
 如果 Windows 錯誤報告的系統設定來啟用報告，自動傳送給 Microsoft 報告內部編譯器錯誤。  
  
## <a name="remarks"></a>備註  
 編譯器無法處理原始程式碼檔案時，就會出現編譯器內部錯誤 (ICE)。 發生 ICE 時，編譯器不會產生輸出檔或任何有用的診斷，無法讓您修正程式碼。  
  
 在舊版本中，有冰，您是鼓勵致電 Microsoft 產品支援服務以報告問題。 與**/errorReport**，您可以直接向 Microsoft 提供 ICE 資訊。 您的錯誤報告有助於改善未來的編譯器版本。  
  
 使用者能否傳送報告，取決於電腦和使用者原則權限。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 [C/C++]  資料夾。  
  
3.  按一下**進階**屬性頁。  
  
4.  修改**錯誤報告**屬性。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ErrorReporting%2A>。  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)