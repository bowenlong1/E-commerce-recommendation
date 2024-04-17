Sub Checkboxes_s3()
    Dim ws As Worksheet
    Dim cb As CheckBox
    Dim i As Integer
    Dim cellWidth As Double
    Dim cellHeight As Double
    Dim rowNum As Integer
    Dim colNum As Integer
    
    ' Set the worksheet
    Set ws = ThisWorkbook.Sheets("v1")
    
    ' Loop through the rows
    For rowNum = 3 To 17 ' Adjust the range as needed
        ' Loop through the columns
        For colNum = 10 To 15 ' Columns J to O
            ' Set position for each checkbox at the center of the cell
            cellWidth = ws.Cells(rowNum, colNum).Width
            cellHeight = ws.Cells(rowNum, colNum).Height
            
            ' Create a checkbox
            Set cb = ws.CheckBoxes.Add(ws.Cells(rowNum, colNum).Left + (cellWidth - 50) / 2, _
                                       ws.Cells(rowNum, colNum).Top + (cellHeight - 20) / 2, 50, 20)
            
            ' Link each checkbox to the corresponding cell
            cb.LinkedCell = ws.Cells(rowNum, colNum).Address
            
            ' Customize checkbox appearance
            cb.Text = "" ' Remove default text
        Next colNum
    Next rowNum
End Sub
