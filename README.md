Sub LinkExistingCheckboxes()
    Dim ws As Worksheet
    Dim cb As CheckBox
    Dim i As Integer
    
    ' Set the worksheet
    Set ws = ThisWorkbook.Sheets("YourSheetName") ' Replace "YourSheetName" with the actual sheet name
    
    ' Loop through the checkboxes in columns I to N
    For i = 3 To 92 ' Adjust the range as needed
        ' Link each existing checkbox to the corresponding cell in columns U to Z
        For j = 0 To 5
            Set cb = ws.CheckBoxes(ws.CheckBoxes.Count + 1) ' Reference the next checkbox
            
            ' Link the checkbox to the corresponding cell in columns U to Z
            cb.LinkedCell = ws.Cells(i, 21 + j).Address ' Column U is the 21st column
            
            ' Customize checkbox appearance (optional)
            cb.Text = "" ' Remove default text
        Next j
    Next i
End Sub
