Sub LinkExistingCheckboxes()
    Dim ws As Worksheet
    Dim cb As CheckBox
    Dim i As Integer
    Dim checkboxIndex As Integer
    
    ' Set the worksheet
    Set ws = ThisWorkbook.Sheets("YourSheetName") ' Replace "YourSheetName" with the actual sheet name
    
    ' Initialize checkbox index
    checkboxIndex = 1
    
    ' Loop through the checkboxes in columns I to N
    For i = 3 To 92 ' Adjust the range as needed
        ' Link each existing checkbox to the corresponding cell in columns U to Z
        For j = 0 To 5
            ' Reference the existing checkbox using the index
            Set cb = ws.CheckBoxes(checkboxIndex)
            
            ' Link the checkbox to the corresponding cell in columns U to Z
            cb.LinkedCell = ws.Cells(i, 21 + j).Address ' Column U is the 21st column
            
            ' Customize checkbox appearance (optional)
            cb.Text = "" ' Remove default text
            
            ' Increment the checkbox index for the next iteration
            checkboxIndex = checkboxIndex + 1
        Next j
    Next i
End Sub
