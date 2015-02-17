{{{
  "title": "Get Blueprints",
  "date": "9-26-2014",
  "author": "Troy Schneringer",
  "attachments": []
}}}

Gets a list of all Blueprints with the specified search criteria.

## URL

    REST:https://api.tier3.com/REST/Blueprint/GetBlueprints/<format>
    SOAP: https://api.tier3.com/SOAP/Blueprints.asmx?op=GetBlueprintsResponseMsg

## Request

### Attributes

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Type</th>
      <th>Description</th>
      <th>Req.</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>CompanySize</td>
      <td>Int</td>
      <td>
        <p>The target company size the of the Blueprint</p>
        <p>1 = 1 - 100
          <br />2 = 101 - 1,000
          <br />3 = 1,001 - 5,000
          <br />4 = &nbsp;5,000+</p>
      </td>
      <td>
        <p>No</p>
      </td>
    </tr>
    <tr>
      <td>OperatingSystems</td>
      <td>Int[]</td>
      <td>
        <p>A list of the operating systems that a Blueprint contains</p>
        <p>Cent OS - 32 bit = 6
          <br />Cent OS - 64 bit = 7
          <br />Debian - 64 bit = 21
          <br />Free BSD - 32 bit = 13
          <br />Free BSD - 64 bit = 14
          <br />Ubuntu - 32 bit = 19
          <br />Ubuntu - 64 bit = 20
          <br />Windows 2003 Enterprise - 32 bit = 15
          <br />Windows 2003 Enterprise - 64 bit = 16
          <br />Windows 2003 - 32 bit = 2
          <br />Windows 2003 - 64 bit = 3
          <br />Windows 2008 - 32 bit = 4
          <br />Windows 2008 - 64 bit = 5
          <br />Windows 2008 Enterprise - 32 bit = 17
          <br />Windows 2008 Enterprise - 64 bit = 18</p>
      </td>
      <td>&nbsp;No</td>
    </tr>
    <tr>
      <td>Search</td>
      <td>String</td>
      <td>
        <p>A keyword search within the Name and Description of the Blueprint&nbsp;</p>
      </td>
      <td>
        <p>No</p>
      </td>
    </tr>
    <tr>
      <td>Visibility</td>
      <td>Int</td>
      <td>
        <p>The visibility level of the Blueprint</p>
        <p>1 = Public
          <br />2 = Private
          <br />3 = Private Shared</p>
      </td>
      <td>
        <p>No</p>
      </td>
    </tr>
  </tbody>
</table>

### Examples

#### JSON

    {

      "CompanySize": "2",

      "OperatingSystems": [ 4, 5, 17, 18],

      "Search": "High Performance",

      "Visibility": 1

    }

#### XML

    <GetBlueprintsRequest>

          <CompanySize>2</CompanySize>

          <OperatingSystems>

              <OS>4</OS>

              <OS>5</OS>

              <OS>17</OS>

              <OS>18</OS>

          </OperatingSystems>

          <Search>High Performance</Search>

          <Visibility>1</Visibility>

    </GetBlueprintsRequest>

## Response

### Attributes

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Success</td>
      <td>Boolean</td>
      <td>True if the request was successful, otherwise False.</td>
    </tr>
    <tr>
      <td>Message</td>
      <td>String</td>
      <td>A description of the result. The contents of this field does not contain any actionable information, it is purely intended to provide a human readable description of the result.</td>
    </tr>
    <tr>
      <td>StatusCode</td>
      <td>Int</td>
      <td>This value will help to identify any errors which were encountered while processing the request. The value of '0' indicates success, all non-zero StatusCodes indicate an error state.</td>
    </tr>
    <tr>
      <td>Blueprints</td>
      <td>Complex (see below)</td>
      <td>A list of Blueprints (see below)</td>
    </tr>
  </tbody>
</table>

### Blueprint Attributes

<table>
  <thead>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
</thead>
<tbody>
    <tr>
      <td>ID</td>
      <td>Int</td>
      <td>The ID of the Blueprint.</td>
    </tr>
    <tr>
      <td>Name</td>
      <td>String</td>
      <td>The name of the Blueprint.</td>
    </tr>
  </tbody>
</table>

### Examples

#### JSON

    {

      "Blueprints":[

        {"ID":1,"Name":"Blueprint 01"},

        {"ID":2,"Name":"Blueprint 02"},

      ], 

      "Success":true,

      "Message":"Success",

      "StatusCode":0

    }

#### XML

    <GetBlueprintsResponse Success="true" Message="Success" StatusCode="0">

        <Blueprints>

            <Blueprint ID="1" Name="Blueprint 01" />

            <Blueprint ID="2" Name="Blueprint 02" />

        </Blueprints>

    </GetBlueprintsResponse>


### Status Codes

<table>
  <thead>
    <tr>
      <th>Status Code</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>Request was successfully processed</td>
    </tr>
    <tr>
      <td>2</td>
      <td>Unknown Error - An application error occurred processing your request, contact Tier3 support to resolve the issue.</td>
    </tr>
    <tr>
      <td>3</td>
      <td>Invalid Request Format. This value indicates that the XML or JSON requests do not match the expected format.</td>
    </tr>
    <tr>
      <td>100</td>
      <td>Authentication Failed - You must logon to the API prior to calling this method.</td>
    </tr>
    <tr>
      <td>1201</td>
      <td>The Visibility value is missing or invalid.</td>
    </tr>
  </tbody>
</table>