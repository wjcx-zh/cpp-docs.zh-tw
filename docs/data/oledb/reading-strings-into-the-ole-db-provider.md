---
title: "將字串讀入 OLE DB 提供者內 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB 提供者, 讀取字串至"
ms.assetid: 517f322c-f37e-4eed-bf5e-dd9a412c2f98
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 將字串讀入 OLE DB 提供者內
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`RMyProviderRowset::Execute` 函式可開啟檔案並讀取字串。  消費者會呼叫 [ICommandText::SetCommandText](https://msdn.microsoft.com/en-us/library/ms709757.aspx)，將檔名傳遞給提供者。  提供者將接收檔名，並將它儲存於成員變數 `m_szCommandText` 內。  `Execute` 會從 `m_szCommandText` 讀取檔名。  如果檔名無效，或檔案無法使用，`Execute` 將會傳回錯誤。  否則，它會開啟檔案，並呼叫 `fgets` 來擷取字串。  `Execute` 每讀到一組字串，都會建立使用者資料錄 \(`CAgentMan`\) 的執行個體，並將它置於陣列。  
  
 如果無法開啟檔案，`Execute` 必定會傳回 **DB\_E\_NOTABLE**。  相反地，如果傳回的是 **E\_FAIL**，提供者將不會對許多消費者產生作用，並且無法通過 OLE DB 的[一致性測試](../../data/oledb/testing-your-provider.md)。  
  
## 範例  
  
### 說明  
 已編輯的 `Execute` 函式類似下列所示：  
  
### 程式碼  
  
```  
/////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
class RMyProviderRowset : public CRowsetImpl< RMyProviderRowset, CAgentMan, CRMyProviderCommand>  
{  
public:  
    HRESULT Execute(DBPARAMS * pParams, LONG* pcRowsAffected)  
    {  
        enum {  
            sizeOfBuffer = 256,  
            sizeOfFile = MAX_PATH  
        };  
        USES_CONVERSION;  
        FILE* pFile = NULL;  
        TCHAR szString[sizeOfBuffer];  
        TCHAR szFile[sizeOfFile];  
        size_t nLength;        errcodeerr;  
  
        ObjectLock lock(this);  
  
        // From a filename, passed in as a command text, scan the file  
        // placing data in the data array.  
        if (!m_szCommandText)  
        {  
            ATLTRACE("No filename specified");  
            return E_FAIL;  
        }  
  
        // Open the file  
        _tcscpy_s(szFile, sizeOfFile, m_szCommandText);  
        if (szFile[0] == _T('\0') ||   
            ((err = fopen_s(&pFile, &szFile[0], "r")) == 0))  
        {  
            ATLTRACE("Could not open file");  
            return DB_E_NOTABLE;  
        }  
  
        // Scan and parse the file.  
        // The file should contain two strings per record  
        LONG cFiles = 0;  
        while (fgets(szString, sizeOfBuffer, pFile) != NULL)  
        {  
            nLength = strnlen(szString, sizeOfBuffer);  
            szString[nLength-1] = '\0';   // Strip off trailing CR/LF  
            CAgentMan am;  
            _tcscpy_s(am.szCommand, am.sizeOfCommand, szString);  
            _tcscpy_s(am.szCommand2, am.sizeOfCommand2, szString);  
  
            if (fgets(szString, sizeOfBuffer, pFile) != NULL)  
            {  
                nLength = strnlen(szString, sizeOfBuffer);  
                szString[nLength-1] = '\0'; // Strip off trailing CR/LF  
                _tcscpy_s(am.szText, am.sizeOfText, szString);  
                _tcscpy_s(am.szText2, am.sizeOfText2, szString);  
            }  
  
            am.dwBookmark = ++cFiles;  
            if (!m_rgRowData.Add(am))  
            {  
                ATLTRACE("Couldn't add data to array");  
                fclose(pFile);  
                return E_FAIL;  
            }  
        }  
  
        if (pcRowsAffected != NULL)  
            *pcRowsAffected = cFiles;  
        return S_OK;  
    }  
}  
```  
  
## 請參閱  
 [實作簡單唯讀提供者](../../data/oledb/implementing-the-simple-read-only-provider.md)