---
title: "引發軟體例外狀況 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "錯誤 [C++], 視為例外狀況"
  - "例外狀況處理, 偵測錯誤"
  - "例外狀況處理, 錯誤做為例外狀況"
  - "例外狀況, 將錯誤標幟為例外狀況"
  - "例外狀況, 軟體"
  - "格式 [C++], 例外狀況代碼"
  - "RaiseException 函式"
  - "執行階段錯誤, 視為例外狀況"
  - "軟體例外狀況"
  - "結構化例外狀況處理, 錯誤做為例外狀況"
ms.assetid: be1376c3-c46a-4f52-ad1d-c2362840746a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 引發軟體例外狀況
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

某些常見的程式錯誤來源是系統未標示為例外狀況。  例如，如果您嘗試配置記憶體區塊，但是沒有足夠的記憶體，執行階段或 API 函式不會引發例外狀況，而是傳回錯誤碼。  
  
 不過，您可以藉由在程式中偵測某種情況，然後呼叫 [RaiseException](http://msdn.microsoft.com/library/windows/desktop/ms680552) 函式回報該情況的方式，將任何情況都視為例外狀況。  以這種方式標幟錯誤，您就可以將結構化例外狀況處理的優點運用到任何類型的執行階段錯誤。  
  
 若要使用結構化例外狀況處理錯誤：  
  
-   定義您自己的事件例外狀況代碼。  
  
-   當您偵測到問題時，呼叫 **RaiseException**。  
  
-   使用例外狀況處理篩選條件測試您所定義的例外狀況代碼。  
  
 WINERROR.H 檔案會顯示例外狀況代碼的格式。  為確保您定義的代碼不會與現有的例外狀況代碼發生衝突，請將第三個最高有效位元設為 1。  四個最高有效位元都應該依照下表所示進行設定。  
  
|位元|建議的二進位設定|說明|  
|--------|--------------|--------|  
|31\-30|11|這兩個位元負責描述程式碼的基本狀態：11 \= 錯誤、00 \= 成功、01 \= 告知性、10 \= 警告。|  
|29|1|用戶端位元。  設為 1，表示使用者定義的程式碼。|  
|28|0|保留位元 \(保持設為 0\)。|  
  
 您可以將前兩個位元設定為 11 二進位以外的設定 \(如果您想要這樣做\)，不過「錯誤」設定適用於大部分例外狀況。  重要的是，記得依照上表所示設定位元 29 和 28。  
  
 這樣一來，產生的錯誤碼最高的四個位元應該會設為十六進位 E。  例如，下列定義所定義的例外狀況代碼不會與任何 Windows 例外狀況代碼發生衝突 \(不過，您可能需要查看協力廠商 DLL 使用哪些代碼\)。  
  
```  
#define STATUS_INSUFFICIENT_MEM       0xE0000001  
#define STATUS_FILE_BAD_FORMAT        0xE0000002  
```  
  
 定義例外狀況代碼之後，就可以用它來引發例外狀況。  例如，下列代碼會引發 STATUS\_INSUFFICIENT\_MEM 例外狀況，以回應記憶體配置問題：  
  
```  
lpstr = _malloc( nBufferSize );  
if (lpstr == NULL)  
    RaiseException( STATUS_INSUFFICIENT_MEM, 0, 0, 0);  
```  
  
 如果您只想要引發例外狀況，可以將最後三個參數設為 0。  在傳遞額外資訊以及設定旗標防止處理常式繼續執行時，最後三個參數會很有用。  如需詳細資訊，請參閱 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] 中的 [RaiseException](http://msdn.microsoft.com/library/windows/desktop/ms680552) 函式。  
  
 然後就可以在您的例外狀況處理篩選條件中，測試您所定義的代碼。  例如：  
  
```  
__try {  
    ...  
}  
__except (GetExceptionCode() == STATUS_INSUFFICIENT_MEM ||  
        GetExceptionCode() == STATUS_FILE_BAD_FORMAT )  
```  
  
## 請參閱  
 [撰寫例外狀況處理常式](../cpp/writing-an-exception-handler.md)   
 [結構化例外狀況處理](../cpp/structured-exception-handling-c-cpp.md)