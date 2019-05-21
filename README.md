![Ekran Alıntısı](https://user-images.githubusercontent.com/29266933/58093674-af417b00-7bd7-11e9-96ea-7e790893427e.PNG)
![Ekran Alıntısı_1](https://user-images.githubusercontent.com/29266933/58093677-af417b00-7bd7-11e9-9920-b55a085f5240.PNG)

```sh

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
        
```
