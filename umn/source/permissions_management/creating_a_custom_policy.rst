:original_name: dds_03_0061.html

.. _dds_03_0061:

Creating a Custom Policy
========================

Custom policies can be created as a supplement to the system policies of DDS. For the actions supported for custom policies, see `DDS Actions <https://docs.otc.t-systems.com/usermanual/iam/en-us_topic_0274187246.html>`__.

You can create custom policies in either of the following ways:

-  Visual editor: Select cloud services, actions, resources, and request conditions. This does not require knowledge of policy syntax.
-  JSON: Edit JSON policies from scratch or based on an existing policy.

For details, see Creating a Custom Policy. The following section contains examples of common DDS custom policies.

Example Custom Policies
-----------------------

-  Example 1: Allowing users to create DDS DB instances

   .. code-block:: text

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "dds:instance:create"
                  ]
              }
          ]
      }

-  Example 2: Denying DDS DB instance deletion

   A deny policy must be used in conjunction with other policies to take effect. If the permissions assigned to a user contain both "Allow" and "Deny", the "Deny" permissions take precedence over the "Allow" permissions.

   The following method can be used if you need to assign permissions of the **DDS FullAccess** policy to a user but also forbid the user from deleting DDS DB instances. Create a custom policy for denying DDS DB instance deletion, and assign both policies to the group the user belongs to. Then the user can perform all operations on DDS except deleting DDS instances. The following is an example deny policy:

   .. code-block:: text

      {
          "Version": "1.1",
          "Statement": [
              {
                "Effect": "Deny"
                "Action": [
                      "dds:instance:deleteInstance"
                  ],
                }
          ]
      }

-  Example 3: Defining permissions for multiple services in a policy

   A custom policy can contain actions of multiple services that are all of the global or project-level type. The following is an example policy containing actions of multiple services:

   .. code-block:: text

      {
              "Version": "1.1",
              "Statement": [
                      {
                              "Action": [
                                      "dds:instance:create",
                                      "dds:instance:modify",
                                      "dds:instance:deleteInstance",
                       "vpc:publicIps:list",
                       "vpc:publicIps:update"
                              ],
                              "Effect": "Allow"
                      }
              ]
      }

-  Example 4: Setting resource policies

   A custom policy can be used to set resource policies, indicating the operation permissions on the resources under the current action. Currently, the instance name can be configured, and the asterisk (*) can be used as a wildcard. The following is an example resource policy:

   .. code-block:: text

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "dds:instance:list"
                  ]
              },
              {
                  "Effect": "Allow",
                  "Action": [
                      "dds:instance:modify"
                  ],
                  "Resource": [
                      "DDS:*:*:instanceName:dds-*"
                  ]
              }
          ]
      }
