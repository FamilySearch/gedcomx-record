# Processing a GEDCOM X Record Set

A GEDCOM X record set file represents an indexed historical record. It will include a source description, a person (for each persona in the record), and relationships.  The following table outlines some elements you may need to find as you consume the data. The formal Gedcom X specification is [here] (/blob/master/specifications/record-specification.md).

### Example Heading

<table class="table table-striped">

      <thead>
      <tr>
        <th>To find:</th>
        <th>Do this:</th>
      </tr>
      </thead>

      <tbody>
      <tr>
        <td>Record Title</td>
        <td>
          <ol>
            <li>
              Find the description of the record.
              <ul>
                <li>The record's <code>description</code> property will contain a reference. Resolve this reference to the <code>id</code> of the <code>sourceDescription</code>.</li>
              </ul>
            </li>
            <li>Look at the <code>title</code> property of the <code>sourceDescription</code>.</li>
          </ol>
          <h4>Example</h4>
          <pre>
&lt;record description="#7">
  ...
  &lt;sourceDescription ... id="7"&gt
    &lt;title>Record 7&lt;/title>
  &lt;/sourceDescription>
  ...
&lt;/record>
          </pre>
        </td>
      </tr>
      <tr>
        <td>Collection Title</td>
        <td>
         <ol>
            <li>Find the description of the record.
            <ul>
              <li>The record's <code<description</code> property will contain a reference. Resolve this reference to the <code>sourceDescription id</code>.</li>
            </ul></li>
            <li>The source's <code>componentOf</code> property will contain a <code>description</code> reference to the description of a collection. Resolve this reference to the <code>sourceDescription</code>.</li>
            <li>Look at the <code>title</code> property of the <code>sourceDescription</code>.</li>
          </ol>
          <h4>Example</h4>
          <pre>
&lt;record description="#7">
  ...
  &lt;sourceDescription ... id="7"&gt
    &lt;componentOf description="6"/&gt
  ...
  &lt;/sourceDescription>
  ...
  &lt;sourceDescription ... id="6"&gt  
    &lt;title>Collection 1&lt;/title>
  &lt;/sourceDescription>
  ...
&lt;/record>
        </pre>
       </td>
      </tr>
      <tr>
      <td>Gender of the Principal Person</td>
        <td>
          <ol>
            <li>Find the principal person.
            <ul>
              <li>The principal person is the person where the <code>principal</code> value is set to <code>"true"</code>. </li>
            </ul></li>
            <li>Look at the <code>gender</code> property of the principal person.</li>
          </ol>
          <h4>Example</h4>
          <pre>
&lt;record description="#s1">
  &lt;person id="p_1" ... principal="true">
  ...   
  &lt;gender type="http://gedcomx.org/Female">
  ...
&lt;/record>
      </pre>
    </td>
  </tr>
      <tr>
      <td>Original text of the Gender of the Principal Person as stated on the record</td>
        <td>
          <ol>
            <li>Find the principal person.
            <ul>
              <li>The principal person is the person where the <code>principal</code> value is set to <code>"true"</code>. </li>
            </ul></li>
            <li>Find the <code>gender</code> property.
            <li>Find the <code>field</code> property of type "http://gedcomx.org/Gender".
            <li>Find the <code>value</code> property of type "http://gedcomx.org/Original". </li>
            <li>Look at the <code>text</code> property of that <code>value</code> property.</li>
          </ol>
          <h4>Example</h4>
          <pre>
&lt;record description="#s1">
  &lt;person id="p_1" ... principal="true">
  ...   
   &lt;gender type="http://gedcomx.org/Female">
    &lt;field type="http://gedcomx.org/Gender">
     &lt;value type="http://gedcomx.org/Original" ...>
      &lt;text>F&lt;/text>
  ...
&lt;/record>
    </pre>
   </td>
  </tr>
      <tr>
      <td>Interpreted text of the Gender of the Principal Person as stated on the record</td>
        <td>
          <ol>
            <li>Find the principal person.
            <ul>
              <li>The principal person is the person where the <code>principal</code> value is set to <code>"true"</code>. </li>
            </ul></li>
            <li>Find the <code>gender</code> property.
            <li>Find the <code>field</code> property of type "http://gedcomx.org/Gender".
            <li>Find the <code>value</code> property of type "http://gedcomx.org/Interpreted".</li>
            <li>Look at the <code>text</code> property of that <code>value</code> property.</li>
          </ol>
          <h4>Example</h4>
          <pre>
&lt;record description="#s1">
  &lt;person id="p_1" ... principal="true">
  ...   
   &lt;gender type="http://gedcomx.org/Female">
    &lt;field type="http://gedcomx.org/Gender">
     &lt;value type="http://gedcomx.org/Interpreted" ...>
      &lt;text>Female&lt;/text>
  ...
&lt;/record>
          </pre>
        </td>
      </tr>
<tr>
      <td>Persistent Identifier (ARK) for the Principal Person</td>
        <td>
          <ol>
            <li>Find the principal person.
            <ul>
              <li>The principal person is the person where the <code>principal</code> value is set to <code>"true"</code>. </li>
            </ul></li>
            <li>Look at the <code>identifier</code> property of the principal person.</li>
          </ol>
          <h4>Example</h4>
          <pre>
&lt;record description="#s1">
  &lt;person id="p_1" ... principal="true">
  ...   
   &lt;identifier type=" ... /Persistent">https://familysearch.org/ ... >
  ...
&lt;/record>
          </pre>
        </td>
      </tr>
      <tr>
      <td>Residence Place of the Principal Person</td>
        <td>
          <ol>
            <li>Find the principal person.
            <ul>
              <li>The principal person is the person where the <code>principal</code> value is set to <code>"true"</code>. </li>
            </ul></li>
            <li>Find the Residence <code>fact</code> of the principal person.
            <ul>
            <li>The Residence <code>fact</code> is the fact of type "http://gedcomx.org/Residence".</li>
            </ul></li>
            <li>Find the <code>place</code> property of the Residence fact.</li>
            <li>Look at the <code>original</code> property to find the residence of the principal person.</li>
            </ol>
          <h4>Example</h4>
          <pre>
&lt;record description="#s1">
  &lt;person id="p_1" ... principal="true">
  ...   
   &lt;fact type="http://gedcomx.org/Residence" ... >
    &lt;place>
     &lt;original>Blandford-Forum, Blandford,Forum, Dorset, England>
  ...
&lt;/record>
          </pre>
        </td>
      </tr>
      <tr>
      <td>Birth Date of the Principal Person</td>
        <td>
          <ol>
            <li>Find the principal person.
            <ul>
              <li>The principal person is the person where the <code>principal</code> value is set to <code>"true"</code>. </li>
            </ul></li>
            <li>Find the Birth <code>fact</code> of the principal person.
            <ul>
            <li>The Birth <code>fact</code> is the fact of type "http://gedcomx.org/Birth".</li>
            </ul></li>
            <li>Find the <code>date</code> property of the Birth fact.</li>
            <li>Look at the <code>original</code> property to find the birth date of the principal person.</li>
            </ol>
          <h4>Example</h4>
          <pre>
&lt;record description="#s1">
  &lt;person id="p_1" ... principal="true">
  ...   
   &lt;fact type="http://gedcomx.org/Birth" ... >
    &lt;date>
     &lt;original>1763>
  ...
&lt;/record>
          </pre>
        </td>
      </tr>
      <tr>
      <td>Surname of the Principal Person</td>
        <td>
          <ol>
            <li>Find the principal person.
            <ul>
              <li>The principal person is the person where the <code>principal</code> value is set to <code>"true"</code>. </li>
            </ul></li>
            <li>Find the <code>name</code> property of the principal person.</li>
            <li>Find the <code>part</code> property with a <code>field</code> value of "http://gedcomx.org/Surname".</li>
            <li>Find the <code>value</code> property of type "http://gedcomx.org/Original".</li>
            <li>Look at the <code>text</code> property of that <code>value</code> property to find the surname of the principal person.</li>
          </ol>
          <h4>Example</h4>
          <pre>
&lt;record description="#s1">
  &lt;person id="p_1"> ... principal="true">
  ...   
   &lt;name type="http://gedcomx.org/BirthName">
    &lt;part type=" ... ">
      &lt;field type="http://gedcomx.org/Surname">
       &lt;value type="http://gedcomx.org/Original" ... >
        &lt;text>Baker&lt;/text>
  ...
&lt;/record>
          </pre>
        </td>
      </tr>
        <td>Marriage Place of a Couple</td>
        <td>
          <ol>
            <li>Find the <code>relationship</code> type that has a value of "http://gedcomx.org/Couple".
            <ul>
              <li>The relationship type's <code>resource</code> property will contain two references. Resolve each reference to the <code>person id</code>.</li>
            </ul></li>
            <li>Find the Marriage <code>fact</code>.
            <ul>
            <li>The Marriage <code>fact</code> is the fact of type "http://gedcomx.org/Marriage".</li>
            </ul></li>
            <li>Find the <code>place</code> property of the Marriage fact.</li>
            <li>Look at the <code>original</code> property to find the marriage place of a couple.</li>
          </ol>
          <h4>Example</h4>
          <pre>
&lt;record description="#s29">
  &lt;relationship type="http://gedcomx.org/Couple">
   &lt;person1 resource="#p_61"/>
   &lt;person2 resource="#p_62"/>  
   &lt;fact type="http://gedcomx.org/Marriage" ... >
    &lt;place>
     &lt;original>Bridport, Bridport, Dorset, England>
  ...
&lt;/record>
          </pre>
        </td>
      </tr>
      </tbody>
      </table>
      
## Process the metadata file

<table class="table table-striped">

      <thead>
      <tr>
        <th>To find:</th>
        <th>Do this:</th>
      </tr>
      </thead>

      <tbody>
      <tr>
        <td>Time Span of Collection</td>
        <td>
          <ol>
            <li>Find the description of the metadata.
            <ul>
              <li>The metadata's <code>description</code> property will contain a reference. Resolve this reference to the <code>sourceDescription id</code>.</li>
            </ul></li>
            <li>Find the <code>coverage</code> property.</li>
            <li>Look at the <code>original</code> or <code>formal</code> value(s) of the <code>temporal</code> property. (For more information on date formats, see the Gedcom X date format <a href="https://github.com/FamilySearch/gedcomx/blob/master/specifications/date-format-specification.md">spec</a>.)</li>
          </ol>
          <h4>Example</h4>
          <pre>
&lt;metadata description="#src_1">
  ...
  &lt;sourceDescription ... id="src_1"&gt
    &lt;coverage>
     &lt;temporal>
      &lt;original>1538/1910&lt;/original>
      &lt;formal>+1538/+1910&lt;/formal>
     &lt;/temporal>
   &lt;/coverage>
  &lt;/sourceDescription>
  ...
&lt;/metadata>
          </pre>
        </td>
      </tr>
      <tr>
        <td>Geographic Location of Collection</td>
        <td>
          <ol>
            <li>Find the description of the metadata.
            <ul>
              <li>The metadata's <code>description</code> property will contain a reference. Resolve this reference to the <code>sourceDescription id</code>.</li>
            </ul></li>
            <li>Find the <code>coverage</code> property.</li>
            <li>Find the <code>spatial description</code> property.
            <ul>
              <li>The metadata's <code>spatial description</code> property will contain a reference. Resolve this reference to the <code>place id</code>.</li>
            </ul></li>
            <li>Look at the <code>name</code> value of that property to find the geographic location of the collection.</li>
          </ol>
          <h4>Example</h4>
          <pre>
&lt;metadata description="#src_1">
  ...
  &lt;sourceDescription ... id="src_1"&gt
    &lt;coverage>
     &lt;spatial description = #place_1986340-1927925>
  ...
    &lt;/spatial>
    &lt;/coverage>
   &lt;place id="place_1986340-1927925">
  ...
   &lt;name xml:lang="en-US">Dorset, England&lt;/name>
   &lt;/place>
  &lt;/sourceDescription>
  ...
&lt;/metadata>
        </pre>
       </td>
      </tr>
       <tr>
        <td>Japanese label for the "PR_NAME" field</td>
        <td>
          <ol>
            <li>Find the <code>recordDescriptor ID</code> of the metadata.</li>
            <li>Find the <code>field</code> property with a <code>value</code> type of "http://gedcomx.org/Interpreted".</li>
            <li>Look at the value of the <code>xml:lang="ja"</code> label. </li>
          </ol>
          <h4>Example</h4>
          <pre>
&lt;recordDescriptor id="rd_1910806">
  &lt;field&gt
    &lt;value type="http://gedcomx.org/Interpreted" ... >
     &lt;label xml:lang="ja">名前&lt;/label>
  ...
&lt;/recordDescriptor>
        </pre>
       </td>
      </tr>
      </tbody>
      </table>

<h3>Another Heading</h3>

header|header2|header3
------|-------|-------
item1|some text|another text
item1|some text|another text
item1|some text|another text
item1|some text|another text
item1|some text|another text
item1|some text|another text
