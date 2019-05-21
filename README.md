# CSharp-TreeviewCheck-DatagridFilter
                                        
                                            1- Filtering system graphic image
                                          
       ![Ekran Alıntısı](https://user-images.githubusercontent.com/29266933/58093176-a7cda200-7bd6-11e9-9602-a2af41d18691.PNG)
       
       TreeView AfterCheck event code
       string[] parcala;
        string filtre = "";
        private void treeView1_AfterCheck(object sender, TreeViewEventArgs e)
        {
            bool x = false;
            filtre = "";
            for (int i = 0; i < treeView1.Nodes.Count; i++)
            {
                if (treeView1.Nodes[i].Text == e.Node.Text)
                {
                    x = true;
                }
            }

            if (x == false)
            {
                parcala = e.Node.FullPath.Split('\\');
                for (int i = 0; i < treeView1.Nodes.Count; i++)
                {
                    if (treeView1.Nodes[i].Text == parcala[0].ToString())
                    {
                        for (int k = 0; k < treeView1.Nodes[i].Nodes.Count; k++)
                        {
                            if (treeView1.Nodes[i].Nodes[k].Checked == true)
                            {
                                if (filtre == "")
                                {
                                    filtre = "'" + treeView1.Nodes[i].Nodes[k].Text + "'";
                                }
                                else
                                {
                                    filtre += ",'" + treeView1.Nodes[i].Nodes[k].Text + "'";
                                }
                            }
                        }
                    }
                }
            }
        }
        
                                                           2 - Apply Button
                                                    
       ![Ekran Alıntısı_1](https://user-images.githubusercontent.com/29266933/58093178-a7cda200-7bd6-11e9-94f3-16d0675c4e80.PNG)
       
       Button Code
             MessageBox.Show(parcala[0] + " --- " + filtre);
            filterView(parcala[0], filtre);
            
----------------------------------------------------------------------------------
       private void filterView(string kolonadi, string secilen)
        {
            for (int i = 0; i < dizi.Length; i++)
            {
                if (dizi[i].ToString() == kolonadi)
                {
                    dataView.RowFilter = anatable.Columns[i] + " IN (" + secilen + ") ";
                    dataGridView1.DataSource = dataView;
                }
            }
        } 
        
