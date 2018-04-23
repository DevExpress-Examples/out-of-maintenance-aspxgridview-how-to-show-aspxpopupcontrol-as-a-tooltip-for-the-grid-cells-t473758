# ASPxGridView - How to show ASPxPopupControl as a tooltip for the grid cells


<p>This example illustrates how to show ASPxPopupControl instead of a standard cell tooltip. </p>


<h3>Description</h3>

<p>To implement this task, perform the following steps:<br>1. Create ASPxPopupControl with ASPxLabel inside:</p>
<code lang="aspx">&lt;dx:ASPxPopupControl ID="ASPxPopupControl1" runat="server" ClientInstanceName="popup" ShowHeader="false"&gt;
    &lt;ContentCollection&gt;
        &lt;dx:PopupControlContentControl runat="server"&gt;
            &lt;dx:ASPxLabel ID="ASPxLabel1" runat="server" Text="ASPxLabel" ClientInstanceName="lbl"&gt;
            &lt;/dx:ASPxLabel&gt;
        &lt;/dx:PopupControlContentControl&gt;
    &lt;/ContentCollection&gt;
&lt;/dx:ASPxPopupControl&gt;
</code>
<p>2. Handle the&nbsp;<a href="https://documentation.devexpress.com/#AspNet/DevExpressWebASPxGridView_HtmlDataCellPreparedtopic">ASPxGridView.HtmlDataCellPrepared</a>&nbsp;event to&nbsp;add the&nbsp;<strong><em>mouseover</em></strong><em>&nbsp;</em>event handler for the grid cells:</p>
<code lang="cs">protected void gridView_HtmlDataCellPrepared(object sender, DevExpress.Web.ASPxGridViewTableDataCellEventArgs e) {
    e.Cell.Attributes.Add("onmouseover",string.Format("onShowPopup(event.x, event.y, '{0}')", e.GetValue("Description")));
}
&nbsp;
</code>
<p>3. Then, you will be able to show a popup with the required information</p>
<code lang="js">function onShowPopup(x, y, text) {
    lbl.SetText(text);
    popup.ShowAtPos(x, y);
}
</code>
<p>&nbsp;</p>

<br/>


