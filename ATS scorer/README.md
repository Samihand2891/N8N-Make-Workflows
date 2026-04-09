#### TO activate using command prompt , give path directory of cv , job description .txt files
`$cv = Get-Content cv.txt -Raw`
`$jd = Get-Content jd.txt -Raw`

`$body = @{`

    cv = $cv
    job_description = $jd
`}` 
| ConvertTo-Json

Invoke-RestMethod -Uri "http://localhost:5678/webhook/ats-optimizer" `
  -Method POST `
  -ContentType "application/json" `
  -Body $body

  -- Take care of gemini api http request key , as most of the time it has server connection issues 
  For that reason I am trying to integrate this into telegram and use AI chatbot instance in n8n 
