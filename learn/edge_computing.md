# Edge Computing

It is often necessary to perform some pre-processing or simple calculation for model measuring points, and such operations can be done by using EnOS Edge.

Edge computing is dependent on the template. Different device types need to use different templates for communication. If the computing logic for a certain device type is edited on a template, you can perform computing for all devices of this certain type by using this template.

In the **EnOS Edge > Template** section, click **edit** . Then you can use the following edge computing functions:

- Point mapping: maps collection points and control points to measuring points defined in the model after processing them using formula. Or directly maps these points to measuring points.
- Script: processes the collection points and control points by using calculation script.

## Point mapping

EnOS provides a set of formulas to process the collection and control points collected from or sent to the device by performing certain operations. Then Edge maps the points to the predefined measuring points in a model.

The list of formulas in EnOS is given as follows. The model measuring points in the list are represented by y, while the collection  and control points are represented by x(i), where i represents the order in which the points are collected.

<<<<<<< Updated upstream
.. list-table::

   * - Formula Name
     - Descriptions
   * - NO_MAPPING
     - Do not map this measuring point to any collection or control point
   * - EQUAL
     - The value of the measuring point is equal to the value of the collection or control point, i.e. y=x
   * - SUM
     - Sum up the value of all the collection points to be the measuring point y=x(1)+x(2)+...+x(i)
   * - PRODUCT
     - Multiply the value of all the collection points to be the measuring point. You can configure an optional coefficient. y=a * x(1) * x(2) * ... * x(i) *
   * - CROSS_PRODUCT
     - Calculate the inner product of all the collection points to be the measuring point. You can configure an optional coefficient (i.e. "Operand" parameter). Note that the order in which the collection points are collected is very important. y=a(x(1) * x(2)+x(3) * x(4)+...+x(i-1) * x(i)
   * - RATIO
     - Calculate the ratio of two collection points to be the measuring point. Note that the order in which the collection points are collected is very important. y=x(1)/x(2)
   * - LOGICAL_OR
     - Perform the logical OR calculation for the collection points to be the measuring point. y=(x(1)|x(2)|...|x(i))
   * - RATIO_AGAINST_SUM
     - Perform the following calculation for three collection points to be the measuring point. y=x(1)/(x(2)+x(3))
   * - BIT_N
     - Take a specified bit out of an AI collection point and copy the bit to a measuring point together with an operand parameter indicating the location of the bit. For example, an operand of 0 indicates that the AI collection point taken is located at the first bit, and an operand of 15 indicates that the AI collection point taken is located at the 16th bit.
   * - BITS_M_TO_N
     - Consecutive multi-bit assignment formula, i.e. take multiple consecutive bits of an AI collection point and assign them to another measuring point together with 2 parameters: operand M (end bit) and operand N (start bit), M>N. For example, if M=7 and N=0, it means taking the 1st to the 8th bit of the collection point and assigning it to the new model point
   * - IF_EQUAL
     - Involve 3 operands. Operand 1 = a, operand 2 = b, operand 3 = c. The calculation is: if x == a, then y== b, else y==c
   * - MULTICHANNEL
     - Map multiple collection points respectively to each component of an array. That is, y is an array: y={y[1], y[2], …, y[i]}, and y[1]=x(1), y[2]=x(2), …, y[i]=x(i), i<=32
   * - MULTIBIT
     - y is an int32 array, and y={y[1],y[2]...,y[i]}, where: y[1].bit0=x(1).bit0, y[1].bit1=x(2).bit0, …, y[1].bit31=x(32).bit0,y[2].bit0=x(33).bit0,y[2].bit1=x(34).bit0,…,y[2].bit31=x(64).bit0,…,y[i].bit0=x(32(i-1)+1).bit0,y[i].bit1=x(32(i-1)+2).bit0,…,y[i].bit31=x(32(i-1)+32).bit0,i<=32

     
=======
.. csv-table::

   "Formula Name", "Descriptions"
   "NO_MAPPING", "Do not map this measuring point to any collection or control point"
   "EQUAL", "The value of the measuring point is equal to the value of the collection or control point, i.e. y=x"
   "SUM", "Sum up the value of all the collection points to be the measuring point y=x(1)+x(2)+...+x(i)"
   "PRODUCT", "Multiply the value of all the collection points to be the measuring point. You can configure an optional coefficient. y=a * x(1) * x(2) * ... * x(i) *"
   "CROSS_PRODUCT", "Calculate the inner product of all the collection points to be the measuring point. You can configure an optional coefficient (i.e. "Operand" parameter). Note that the order in which the collection points are collected is very important. y=a(x(1) * x(2)+x(3) * x(4)+...+x(i-1) * x(i)"
   "RATIO", "Calculate the ratio of two collection points to be the measuring point. Note that the order in which the collection points are collected is very important. y=x(1)/x(2)"
   "LOGICAL_OR", "Perform the logical OR calculation for the collection points to be the measuring point. y=(x(1)|x(2)|...|x(i))"
   "RATIO_AGAINST_SUM", "Perform the following calculation for three collection points to be the measuring point. y=x(1)/(x(2)+x(3))"
   "BIT_N", "Take a specified bit out of an AI collection point and copy the bit to a measuring point together with an operand parameter indicating the location of the bit. For example, an operand of 0 indicates that the AI collection point taken is located at the first bit, and an operand of 15 indicates that the AI collection point taken is located at the 16th bit."
   "BITS_M_TO_N", "Consecutive multi-bit assignment formula, i.e. take multiple consecutive bits of an AI collection point and assign them to another measuring point together with 2 parameters: operand M (end bit) and operand N (start bit), M>N. For example, if M=7 and N=0, it means taking the 1st to the 8th bit of the collection point and assigning it to the new model point"
   "IF_EQUAL", "Involve 3 operands. Operand 1 = a, operand 2 = b, operand 3 = c. The calculation is: if x == a, then y== b, else y==c"
   "MULTICHANNEL", "Map multiple collection points respectively to each component of an array. That is, y is an array: y={y[1], y[2], …, y[i]}, and y[1]=x(1), y[2]=x(2), …, y[i]=x(i), i<=32"
   "MULTIBIT", "y is an int32 array, and y={y[1],y[2]...,y[i]}, where: y[1].bit0=x(1).bit0, y[1].bit1=x(2).bit0, …, y[1].bit31=x(32).bit0,y[2].bit0=x(33).bit0,y[2].bit1=x(34).bit0,…,y[2].bit31=x(64).bit0,…,y[i].bit0=x(32(i-1)+1).bit0,y[i].bit1=x(32(i-1)+2).bit0,…,y[i].bit31=x(32(i-1)+32).bit0,i<=32"

<!--end-->
>>>>>>> Stashed changes

### Formula Applicable To Non-array Measuring Points

For the attributes of non-array measuring points, EnOS supports the following formulas:

- NO_MAPPING
- INVALID
- EQUAL
- SUM
- PRODUCT
- CROSS_PRODUCT
- RATIO
- LOGICAL_OR
- RATION_AGAINST_SUM
- BIT_N
- BITS_M_TO_N
- IF_EQUAL

### Formula Applicable To Array Measuring Points

- NO_MAPPING
- INVALID
- MULTICHANNEL
- MULTIBIT

## Data Processing Scripts

For the syntax of Groovy, see www.groovy-lang.org. Some advanced features of Groovy, such as defining a new class, are disabled in EnOS.

To use Groovy scripts to real-time process device data, EnOS provides some methods that can be used in scripts. Users can apply these methods to read and set measuring point data and read data from devices.

Some of the most commonly used methods are given as follows:

.. csv-table::

   "Methods", "Descriptions"
   "Number input (String domain-point-name)", "Read a measuring point value. The measuring point name is taken as a parameter, and it must match the definition in the device model. The returned value is an integer or float based on the definitions of measuring points in the model"
   "void output (String domain-point-name, Number value)", "Set the value of a measuring point so that 1 data entry is created for 1 measuring point. The measuring point name must match with the definition in the model. The value to be set is an integer or float. EnOS automatically converts the value into the type that matches with the measuring point definition."
   "Boolean attrExists (String attribute-name)", "Used to determine whether an attribute exists or not. The attribute value is taken as a parameter, and it must have been defined in the model."
   "String attrString(String attribute-name)", "Read an attribute value and convert it into a string. The attribute value is taken as a parameter, and it must have been defined in the device model."

### Script samples

- An electric meter's voltage value U = U(0)*10^(P-4), where U(0) and P are the collection points, and U represents the final voltage value. The script sample is given as follows:
   ```groovy
   output("METER3X.UA", input("METER3X.UA_tmp") * (10 ** (input("METER3X.DPT") - 4)))
   ```

- Whenever the inverter reports a specific error code (28 or 38), EnOS generates a data entry of value 1 for measuring point INV.Fault. Whenever the inverter reports other error codes, EnOS generates a data entry of value 0 for INV.Fault The script is given as follows:
  ```groovy
  if (input("INV.FaultCode")==28 || input("INV.FaultCode"=38)
  {
    output("INV.Fault", 1)
  }
  else
  {
    output("INV.Fault", 0)
  }

  ```

- A device whose attribute `invType` is set to `STRING`. When the device receives the data of the multi-way attribute `INV.BranchCurIn`, EnOS calculates its dispersion rate and multiply it by 100 and set it to the `INV.Disperse`. No calculation will be performed for the device whose `invType` attribute does not meet appropriate conditions. The script is given as follows:
  ```groovy
  if (attrExists("invType")&&attrString("invType") == "STRING") {
    output("INV.Disperse", mcCoV("INV.BranchCurIn") * 100.0)
  }

  ```
