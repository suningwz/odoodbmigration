## Guide: How to migrate all objects of the following models from source to a target
  * product.attribute
  * product.attribute.value
  * product.attribute.line
  * product.template
  * product.template.attribute.value
  * product.template.attribute.line
  * product.product 
  * product.public.category
  * product.pricelist
  * product.pricelist.item

### Step 1: Configuration
The code to migrate the objects are in the migrate_objects/ directory.

* In `credentials.py` you need to set the right credentials for the machines you need to access.
* In `configuration.py` you need to change the IP, database name, and credentials of the source and target.

### Step 2: Setup ssh tunnel
Run the scripts from your local machine. You need an ssh tunnel like so: ssh $USER@oden.vertel.se -L 6080:[target IP]:80

### Step 2: Run the scripts in the following order
(actually only 1. needs to be done first, the order of the other scripts are irrelevant)
1. `set_external_id.py`
2. `set_product_category.py`
3. `set_product_pricelist_item.py`
4. `set_category_parent.py`
5. `set_variant_on_template.py` (does not work yet)
